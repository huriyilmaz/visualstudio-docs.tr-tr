---
title: 'Nasıl yapılır: ClickOnce güven Istemi davranışını yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58e5f0e9154137097a94637799966ee94818fca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150826"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Nasıl yapılır: ClickOnce Güven İstemi Davranışını Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce güven istemi ' ni, son kullanıcılara Windows Forms uygulamalar, Windows Presentation Foundation uygulamalar, konsol uygulamaları, WPF tarayıcı uygulamaları ve Office çözümleri gibi ClickOnce uygulamalarını yükleme seçeneği verilip verilmediğini denetlemek için yapılandırabilirsiniz. Her son kullanıcının bilgisayarında kayıt defteri anahtarlarını ayarlayarak güven istemi 'ni yapılandırırsınız.  
  
 Aşağıdaki tabloda, beş bölgenin (Internet, UntrustedSites, Bilgisayarım, LocalIntranet ve TrustedSites) her birine uygulanabilen yapılandırma seçenekleri gösterilmektedir.  
  
|Seçenek|Kayıt defteri ayarı değeri|Açıklama|  
|------------|----------------------------|-----------------|  
|Güven istemi 'ni etkinleştirin.|`Enabled`|ClickOnce güven istemi, son kullanıcıların ClickOnce uygulamalarına güven izni verebilmesi için görüntülenir.|  
|Güven istemi 'ni kısıtlayın.|`AuthenticodeRequired`|ClickOnce güven istemi yalnızca, ClickOnce uygulamaları yayımcıyı tanımlayan bir sertifikayla imzalanmışsa görüntülenir.|  
|Güven isteğini devre dışı bırakın.|`Disabled`|ClickOnce güven istemi, açıkça güvenilen bir sertifikayla imzalanmamış herhangi bir ClickOnce uygulaması için görüntülenmez.|  
  
 Aşağıdaki tabloda her bölge için varsayılan davranış gösterilmektedir. Uygulamalar sütunu Windows Forms uygulamalar, Windows Presentation Foundation uygulamalar, WPF tarayıcı uygulamaları ve konsol uygulamaları anlamına gelir.  
  
|Bölge|Uygulamalar|Office çözümleri|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 ClickOnce güven istemi 'ni etkinleştirerek, kısıtlayarak veya devre dışı bırakarak bu ayarları geçersiz kılabilirsiniz.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>ClickOnce güven Istemi 'ni etkinleştirme  
 Son kullanıcılara, bu bölgeden gelen herhangi bir ClickOnce uygulamasını yükleme ve çalıştırma seçeneği ile sunulmasını istediğinizde, bir bölge için güven istemi 'ni etkinleştirin.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni etkinleştirmek için  
  
1. Kayıt defteri düzenleyicisini açın:   
  
    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.  
  
    2. **Aç** kutusuna `regedit` (veya `regedit32` 32 bit Windows üzerinde) yazın ve ardından **Tamam**' a tıklayın.  
  
2. Aşağıdaki kayıt defteri anahtarını bulun:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Anahtar yoksa, oluşturun.  
  
3. Aşağıdaki tabloda gösterilen ilişkili değerlerle birlikte, zaten mevcut değilse, aşağıdaki alt anahtarları **dize değeri**olarak ekleyin.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Office çözümleri için `Internet` varsayılan değere sahiptir `AuthenticodeRequired` ve `UntrustedSites` değeri vardır `Disabled` . Diğerlerinin tümü için `Internet` varsayılan değer vardır `Enabled` .  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlama yoluyla etkinleştirmek için  
  
1. Visual Studio 'da Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2. Düzenlenmek üzere program. vb veya Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>ClickOnce güven Istemi kısıtlaması  
 Güven istemi 'ni, kullanıcılardan bir güven kararı istenmeden önce bilinen kimliği olan Authenticode sertifikaları ile imzalanması gerekir.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni kısıtlamak için  
  
1. Kayıt defteri düzenleyicisini açın:   
  
    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.  
  
    2. **Aç** kutusuna `regedit` (veya `regedit32` 32 bit Windows üzerinde) yazın ve ardından **Tamam**' a tıklayın.  
  
2. Aşağıdaki kayıt defteri anahtarını bulun:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Anahtar yoksa, oluşturun.  
  
3. Aşağıdaki tabloda gösterilen ilişkili değerlerle birlikte, zaten mevcut değilse, aşağıdaki alt anahtarları **dize değeri**olarak ekleyin.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlı bir şekilde kısıtlamak için  
  
1. Visual Studio 'da Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2. Düzenlenmek üzere program. vb veya Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>ClickOnce güven Istemi 'ni devre dışı bırakma  
 Güven istemi 'ni devre dışı bırakarak, son kullanıcılara güvenlik ilkesinde henüz güvenilmeyen çözümleri yüklemek için seçenek verilmez.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni devre dışı bırakmak için  
  
1. Kayıt defteri düzenleyicisini açın:   
  
    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.  
  
    2. **Aç** kutusuna `regedit` (veya `regedit32` 32 bit Windows üzerinde) yazın ve ardından **Tamam**' a tıklayın.  
  
2. Aşağıdaki kayıt defteri anahtarını bulun:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Anahtar yoksa, oluşturun.  
  
3. Aşağıdaki tabloda gösterilen ilişkili değerlerle birlikte, zaten mevcut değilse, aşağıdaki alt anahtarları **dize değeri**olarak ekleyin.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlı olarak devre dışı bırakmak için  
  
1. Visual Studio 'da Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2. Düzenlenmek üzere program. vb veya Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Nasıl yapılır: Uygulama ve Dağıtım Bildirimlerini Yeniden İmzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
