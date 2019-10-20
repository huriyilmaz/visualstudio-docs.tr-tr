---
title: 'Sorun giderme özel durumları: System. ServiceModel. Security. MessageSecurityException | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b8ce3f16c1439d62cfa1e2cff344b70e6724c42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655361"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Özel Durum Sorunlarını Giderme: System.ServiceModel.Security.MessageSecurityException
@No__t_1 bir iletinin doğru bir şekilde güvenli olmadığını veya üzerinde oynandığını belirlediğinde, <xref:System.ServiceModel.Security.MessageSecurityException> bir özel durum oluşturulur. Aşağıdaki koşullar doğru olduğunda hata en sık meydana gelir:

- Bir Web sitesi veya Web uygulaması projesindeki WCF hizmeti (. svc) ile iletişim kurmak için Uzak Masaüstü Bağlantısı veya Terminal Hizmetleri gibi uzak bir bağlantı üzerinden bir WCF hizmet başvurusu kullanırsınız.

- Uzak site üzerinde yönetici izinleriniz yok.

- Uzak sitedeki localhost 'a gönderilen istekler [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme sunucusu tarafından işlenir.

## <a name="associated-tips"></a>İlişkili Ipuçları
 **ASP.Net geliştirme sunucusunu kullanırken NTLM kimlik doğrulama sorunlarını çözün.**
@No__t_0 geliştirme sunucusu genellikle Windows NT Challenge/Response (NTLM) güvenliği devre dışıdır ve bu da anonim erişime izin verir. Varsayılan olarak, bir Terminal Hizmetleri oturumu çalıştırdığınızda veya uzak bir bağlantı kullandığınızda, NTLM güvenliği etkinleştirilir. NTLM etkinleştirildiğinde, tüm localhost istekleri [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme sunucusunu başlatan kullanıcı veya işlemin kimlik bilgileriyle onaylanır. Bu, güvenlik tehditlerini azaltır. Bununla birlikte, WCF kendi kimlik doğrulamasını da gerçekleştirir ve yönetici olmayan bir hesabın WCF hizmetlerini kullanmasına izin vermez.

 Uzak bir Kullanıcı [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme sunucusunu kullanarak Web sitesini çalıştırabilirler ve ayrıca bir Web hizmeti veya WCF hizmeti ile birlikte çalışarak, özel bir hizmet bağlaması oluşturabilir veya NTLM güvenliğini kapatabilirsiniz.

> [!IMPORTANT]
> NTLM güvenliğini kapatmak önerilmez ve bir güvenlik tehdidi oluşturabilir.

 Özel bir hizmet bağlaması oluşturursanız, NTLM kimlik doğrulaması ile hala korunacaktır.

 WCF hizmeti için özel bir hizmet bağlaması oluşturmak için aşağıdaki adımları kullanın.

#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>ASP.NET Development Server içinde barındırılan WCF hizmeti için özel bir hizmet bağlaması oluşturmak için

1. Özel durumu oluşturan WCF hizmeti için Web. config dosyasını açın.

2. Web. config dosyasına aşağıdaki bilgileri girin.

   ```
   <bindings>
     <customBinding>
       <binding name="Service1Binding">
         <transactionFlow />
         <textMessageEncoding />
         <httpTransport authenticationScheme="Ntlm" />
       </binding>
     </customBinding>
   </bindings>
   ```

3. Web. config dosyasını kaydedin ve kapatın.

4. WCF veya Web hizmeti kodunda, uç nokta değerini aşağıdaki şekilde değiştirin:

   ```
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />
   ```

    Bu, hizmetin özel bağlamayı kullanmasını sağlar.

5. Hizmete erişen web uygulamasındaki hizmete bir başvuru ekleyin. ( **Hizmet başvurusu Ekle** iletişim kutusunda, özel durumu oluşturan özgün hizmette yaptığınız gibi hizmete bir başvuru ekleyin.)

   Bir WCF hizmet başvurusuyla çalışırken NTLM güvenliğini devre dışı bırakmak için aşağıdaki adımları izleyebilirsiniz.

> [!IMPORTANT]
> NTLM güvenliğini kapatmak önerilmez ve bir güvenlik tehdidi oluşturabilir.

#### <a name="to-turn-off-ntlm-security"></a>NTLM güvenliğini devre dışı bırakmak için

1. **Çözüm Gezgini**, Web sitesi adına sağ tıklayın ve ardından **Özellik sayfaları**' na tıklayın.

2. **Başlangıç seçenekleri**' ni seçin ve **NTLM kimlik doğrulaması** onay kutusunu temizleyin.

3. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [özel durum yardımcısını kullanmak](https://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711) <xref:System.ServiceModel.Security.MessageSecurityException>