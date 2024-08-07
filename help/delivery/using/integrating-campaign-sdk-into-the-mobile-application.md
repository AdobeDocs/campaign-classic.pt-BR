---
product: campaign
title: Integrar SDK do Campaign
description: Saiba como integrar o SDK do Campaign ao seu aplicativo móvel
feature: Mobile SDK Integration, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 100%

---

# Integrar o SDK do Campaign ao seu aplicativo {#integrating-campaign-sdk-into-the-mobile-application}

>[!CAUTION]
>
>A Adobe recomenda fortemente o uso do SDK móvel da Adobe Experience Platform através da configuração da extensão do Adobe Campaign na interface da coleção de dados. O SDK móvel da Adobe Experience Platform ajuda a potencializar as soluções e os serviços da Adobe Experience Cloud em seus aplicativos móveis. A configuração dos SDKs é realizada por meio da interface da coleção de dados para oferecer uma configuração flexível e integrações extensíveis baseadas em regras. [Saiba mais na documentação do Adobe Developer](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}

Para obter o SDK do Campaign (antes conhecido como Neolane SDK), entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

Para saber mais sobre as diferentes versões compatíveis com Android e iOS, consulte a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#MobileSDK).

Você encontrará abaixo as etapas para a integração do SDK do Campaign.

+++**Carregamento do SDK do Campaign**

* **No Android**: o arquivo **neolane_sdk-release.aar** deve estar vinculado ao projeto.

  A permissão a seguir concede acesso ao servidor do Adobe Campaign:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  A permissão a seguir possibilita a recuperação do identificador exclusivo de um dispositivo móvel:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  A partir da versão 1.0.24 do SDK, essa permissão é usada somente para versões anteriores a Android 6.0.

  A partir da versão 1.0.26 do SDK, essa permissão não é mais usada.

* **No iOS**: os arquivos **libNeolaneSDK.a** e **Neolane_SDK.h** devem estar vinculados ao projeto. A partir da versão 1.0.24 do SDK, a opção **ENABLE_BITCODE** é ativada.

  >[!NOTE]
  >
  >Para a versão 1.0.25 do SDK, as quatro arquiteturas estão disponíveis no arquivo **Neolane_SDK.h**.

+++

+++**Configurações de integração declarativa**

Para integrar o SDK do Campaign no aplicativo móvel, o administrador funcional deve fornecer as seguintes informações ao desenvolvedor:

* **Uma chave de integração**: para permitir que a plataforma Adobe Campaign identifique o aplicativo móvel.

  >[!NOTE]
  >
  >Essa chave de integração é inserida no console do Adobe Campaign, na guia **[!UICONTROL Information]** do serviço dedicado ao aplicativo móvel. Consulte [Configuração de um aplicativo para dispositivos móveis no Adobe Campaign](configuring-the-mobile-application.md).

* **Um URL de rastreamento**: que corresponde ao endereço do servidor de rastreamento do Adobe Campaign.
* **Um URL de marketing**: para ativar a coleta de assinaturas.

* **No Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **No iOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**Função de registro**

A função de registro permite:

* enviar o ID de notificação ou o ID de envio (deviceToken para iOS e registrationID para Android) para o Adobe Campaign.
* recuperar a chave de reconciliação ou o userKey (email ou número de conta, por exemplo)

* **No Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  Se usa FCM (Firebase Cloud Messaging), recomendamos usar a função **registerDevice** ao chamar a função **onTokenRefresh** para notificar o Adobe Campaign de alteração no token do dispositivo móvel do usuário.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **No iOS**:

  ```
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

+++

+++**Função de rastreamento**

* **No Android**:

  As funções de rastreamento permitem rastrear ativações de notificação (aberturas) e exibições de notificação (captura de tela).

  Para acompanhar a exibição de notificação (realizada ao chamar a função **notifyReceive** do SDK), siga a implementação abaixo. Observe que, quando o FCM (Firebase Cloud Messaging) é usado, recomendamos utilizar a função **notifyReceive** quando a função **onMessageReceived** for chamada pelo sistema Android.

  ```
  package com.android.YourApplication;
  
  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;
  
  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;
  
  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;
  
  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";
  
    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }
  
      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;
  
    // notify Neolane that a notification just arrived
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
    NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
    nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1){}
    });
    if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;
  
        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
  
        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();
  
        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Aqui está um exemplo de implementação para rastreamento de uma abertura de notificação (executada ao chamar a função **notifyOpening** do SDK). A classe **NotificationActivity** corresponde à classe usada para criar o objeto **notifIntent** no exemplo anterior.

  ```
  public class NotificationActivity extends Activity {
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
    }
   }
  }
  ```

* **No iOS**:

  A função de rastreamento permite rastrear quando as notificações são ativadas (abertas).

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >A partir da versão 7.0, uma vez implementada a função **`application:didReceiveRemoteNotification:fetchCompletionHandler`**, o sistema operacional passa a chamar apenas essa função. Portanto, a função **`application:didReceiveRemoteNotification`** não é chamada.

+++

+++**Rastreamento de notificação silenciosa**

O iOS permite enviar notificações silenciosas, uma notificação ou dados que são enviados diretamente para um aplicativo móvel sem exibi-los. O Adobe Campaign permite rastreá-las.

Para rastrear a notificação silenciosa, siga o exemplo abaixo:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

+++

+++**RegisterDeviceStatus delegado**

>[!NOTE]
>
>Observe que isso é exclusivo do iOS.

No iOS, o protocolo delegado permite obter o resultado da chamada **registerDevice** e pode ser usado para saber se ocorreu um erro durante o registro.

O protótipo **registerDeviceStatus** é:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

O **Status** permite saber se um registro foi bem-sucedido ou se ocorreu um erro.

**ErrorReason** fornece mais informações sobre os erros que ocorreram. Para obter mais informações sobre erros disponíveis e suas descrições, consulte a tabela abaixo.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Descrição<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registration Succeeded<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> O nome de host do servidor de marketing ACC está vazio ou não está definido.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> A chave de integração está vazia ou não está definida.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Problema de conexão com o ACC<br /> </td>
   <td> Mais informações (na linguagem atual do SO)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> O UUID fornecido (chave de integração) é desconhecido.<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Erro inesperado retornado ao servidor ACC.<br /> </td>
   <td> A mensagem de erro retornou para o ACC.<br /> </td>
  </tr>
 </tbody>
</table>

A definição do protocolo **Neolane_SDKDelegate** e do delegado **registerDeviceStatus** e a seguinte:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Para implementar o delegado **registerDeviceStatus**, siga estas etapas:

1. Implemente o **setDelegate** durante a inicialização do SDK.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Adicione o protocolo na **@interface** de sua classe.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implemente o delegado no **AppDelegate**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

+++

+++**Variáveis**

As variáveis permitem definir o comportamento do aplicativo móvel após receber uma notificação. Essas variáveis devem ser definidas no código do aplicativo móvel e no console do Adobe Campaign, na guia **[!UICONTROL Variables]** do aplicativo móvel dedicado (consulte [Configuração de um aplicativo móvel no Adobe Campaign](configuring-the-mobile-application.md)). Veja um exemplo de um código que permite que um aplicativo móvel colete quaisquer variáveis adicionadas em uma notificação. No nosso exemplo, estamos usando a variável &quot;VAR&quot;.

* **No Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **No iOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }
  
  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>A Adobe recomenda escolher nomes de variáveis curtos, pois o tamanho da notificação é limitado a 4kB para iOS e Android.

+++

+++**Extensão do serviço de notificação**

**Para iOS**

A mídia deve ser baixada no nível da extensão de serviço de notificação.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

+++

+++**Extensão de Conteúdo de Notificação**

**Para iOS**

Nesse nível, você precisa:

* Associe sua extensão de conteúdo à categoria enviada pelo Adobe Campaign:

  Se quer que seu aplicativo móvel exiba uma imagem, é possível definir o valor da categoria como &quot;imagem&quot; no Adobe Campaign e no aplicativo móvel, criar uma extensão de notificação com o parâmetro **UNNotificationExtensionCategory** definido como &quot;imagem&quot;. Quando a notificação por push é recebida no dispositivo, a extensão é chamada de acordo com o valor da categoria definida.

* Definir o seu layout de notificação

  É necessário definir um layout com os widgets relevantes. Para uma imagem, o widget é denominado **UIImageView**.

* Exibir sua mídia

  É necessário adicionar o código para alimentar os dados de mídia no widget. Veja um exemplo de código para uma imagem:

  ```
  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>
  
  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end
  
  @implementation NotificationViewController
  
  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }
  
  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  ```

+++
