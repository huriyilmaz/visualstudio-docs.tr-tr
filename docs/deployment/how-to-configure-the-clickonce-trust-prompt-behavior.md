---
title: 'Nasıl Yapılandırılır: ClickOnce Trust Prompt Davranışını Yapılandırın | Microsoft Dokümanlar'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649146"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Nasıl yapılandırılır: ClickOnce güven istemi davranışını yapılandırın
Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları, konsol uygulamaları, WPF tarayıcı uygulamaları ve Office çözümleri gibi son kullanıcılara ClickOnce uygulamalarını yükleme seçeneğinin verilip verilmediğini denetlemek için ClickOnce güven istemini yapılandırabilirsiniz. Her son kullanıcının bilgisayarında kayıt defteri anahtarlarını ayarlayarak güven istemini yapılandırAbilirsiniz.

 Aşağıdaki tablo, beş bölge (Internet, UntrustedSites, MyComputer, LocalIntranet ve TrustedSites) her birine uygulanabilecek yapılandırma seçeneklerini gösterir.

|Seçenek|Kayıt defteri ayar değeri|Açıklama|
|------------|----------------------------|-----------------|
|Güven istemini etkinleştirin.|`Enabled`|ClickOnce güven istemi, son kullanıcıların ClickOnce uygulamalarına güven verebilmeleri için görüntülenir.|
|Güven istemini kısıtlayın.|`AuthenticodeRequired`|ClickOnce güven istemi yalnızca ClickOnce uygulamaları yayımcıyı tanımlayan bir sertifikayla imzalanırsa görüntülenir.|
|Güven istemini devre dışı.|`Disabled`|ClickOnce güven istemi, açıkça güvenilen bir sertifikayla imzalanmayan clickonce uygulamaları için görüntülenmez.|

 Aşağıdaki tablo, her bölge için varsayılan davranışı gösterir. Uygulamalar sütunu Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları, WPF tarayıcı uygulamaları ve konsol uygulamaları anlamına gelir.

|Bölge|Uygulamalar|Office çözümleri|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 ClickOnce güven istemini etkinleştirerek, kısıtlayarak veya devre dışı bırakarak bu ayarları geçersiz kılabilirsiniz.

## <a name="enable-the-clickonce-trust-prompt"></a>ClickOnce güven istemini etkinleştirme
 Son kullanıcılara, o bölgeden gelen herhangi bir ClickOnce uygulamasını yükleme ve çalıştırma seçeneğinin sunulmasını istediğinizde, bir bölge için güven istemini etkinleştirin.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemini etkinleştirmek için

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat'ı**tıklatın ve ardından **Çalıştır'ı**tıklatın.

    2. **Aç** kutusuna, `regedit`''yi yazın ve sonra **Tamam'ı**tıklatın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa, oluşturun.

3. Aşağıdaki alt anahtarları **String Değeri**olarak ekleyin , eğer zaten yoksa, aşağıdaki tabloda gösterilen ilişkili değerlerle.

    |String Value alt anahtarı|Değer|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Office çözümleri `Internet` için varsayılan `AuthenticodeRequired` değere `UntrustedSites` ve `Disabled`değere sahiptir. Diğerleri için `Internet` varsayılan değere `Enabled`sahiptir.

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlı olarak etkinleştirmek için

1. Visual Studio'da Visual Basic veya Visual C# konsolu uygulaması oluşturun.

2. Düzenleme için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>ClickOnce güven istemini kısıtlama
 Kullanıcılardan güven kararı istenmeden önce kimliği bilinen Authenticode sertifikalarıyla çözümlerin imzalanması için güven istemini kısıtlayın.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemini kısıtlamak için

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat'ı**tıklatın ve ardından **Çalıştır'ı**tıklatın.

    2. **Aç** kutusuna, `regedit`''yi yazın ve sonra **Tamam'ı**tıklatın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa, oluşturun.

3. Aşağıdaki alt anahtarları **String Değeri**olarak ekleyin , eğer zaten yoksa, aşağıdaki tabloda gösterilen ilişkili değerlerle.

    |String Value alt anahtarı|Değer|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlı olarak kısıtlamak için

1. Visual Studio'da Visual Basic veya Visual C# konsolu uygulaması oluşturun.

2. Düzenleme için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="disable-the-clickonce-trust-prompt"></a>ClickOnce güven istemini devre dışı
 Son kullanıcılara güvenlik ilkelerinde zaten güvenilmeyen çözümleri yükleme seçeneği verilmemesi için güven istemini devre dışı kullanabilirsiniz.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemini devre dışı kılabilir

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat'ı**tıklatın ve ardından **Çalıştır'ı**tıklatın.

    2. **Aç** kutusuna, `regedit`''yi yazın ve sonra **Tamam'ı**tıklatın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa, oluşturun.

3. Aşağıdaki alt anahtarları **String Değeri**olarak ekleyin , eğer zaten yoksa, aşağıdaki tabloda gösterilen ilişkili değerlerle.

    |String Value alt anahtarı|Değer|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce güven istemini programlı olarak devre dışı katmak için

1. Visual Studio'da Visual Basic veya Visual C# konsolu uygulaması oluşturun.

2. Düzenleme için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Nasıl Yapılır: ClickOnce güvenlik ayarlarını etkinleştirin](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapilir: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılsın: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl?](securing-clickonce-applications.md)
- [Nasıl yapIlir: ClickOnce uygulamaları için istemci bilgisayara güvenilir bir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl yapilir: Uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
