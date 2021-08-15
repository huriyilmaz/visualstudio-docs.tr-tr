---
title: ClickOnce İstemi Davranışı'| Microsoft Docs
description: Son kullanıcılara uygulama yükleme ClickOnce olup olmadığını kontrol etmek için güvenlik güven istemini yapılandırmayı ClickOnce öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4bb20f403a41ece1096404c3eec9191bc44d461c38d824a2959204fb6fa7df6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293879"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Nasıl yapılandırılır: ClickOnce istemi davranışını yapılandırma
ClickOnce Forms uygulamaları, Windows Windows Presentation Foundation uygulamaları, konsol uygulamaları, WPF tarayıcı uygulamaları ve Office çözümleri gibi ClickOnce uygulamalarını yükleme seçeneği olup olmadığını kontrol etmek için Windows Presentation Foundation güven istemini yapılandırabilirsiniz. Güven istemini yapılandırmak için her bir son kullanıcının bilgisayarına kayıt defteri anahtarları ayarlarsınız.

 Aşağıdaki tabloda beş bölgenin her biri için uygulanacak yapılandırma seçenekleri (İnternet, UntrustedSites, MyComputer, LocalIntranet ve TrustedSites) gösterir.

|Seçenek|Kayıt defteri ayar değeri|Açıklama|
|------------|----------------------------|-----------------|
|Güven istemini etkinleştirin.|`Enabled`|Son ClickOnce uygulamalara güven izni vermek için tek bir güven ClickOnce görüntülenir.|
|Güven istemini kısıtla.|`AuthenticodeRequired`|Bu ClickOnce istemi, yalnızca ClickOnce yayımcıyı tanımlayan bir sertifikayla imzalanmışsa görüntülenir.|
|Güven istemini devre dışı bırakma.|`Disabled`|Açıkça ClickOnce bir sertifika ile imza ClickOnce herhangi bir uygulama için güvenlik güveni istemi görüntülenmez.|

 Aşağıdaki tabloda her bölge için varsayılan davranış gösterir. Uygulamalar sütunu Form uygulamaları, Windows uygulamaları, WPF Windows Presentation Foundation uygulamaları ve konsol uygulamalarını ifade eder.

|Bölge|Uygulamalar|Office çözümleri|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Güven istemini etkinleştirerek, kısıtlayan veya devre dışı bırakarak bu ClickOnce geçersiz kılabilirsiniz.

## <a name="enable-the-clickonce-trust-prompt"></a>ClickOnce istemini etkinleştirme
 Son kullanıcılara bu bölgeden gelen herhangi bir uygulama yükleme ve çalıştırma seçeneğinin ClickOnce bir bölge için güven istemini etkinleştirin.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini ClickOnce güvenlik istemini etkinleştirmek için

1. Kayıt defteri düzenleyicisini açın:

    1. Başlat **'a** ve ardından **Çalıştır'a tıklayın.**

    2. Aç **kutusuna yazın** ve `regedit` Tamam'a **tıklayın.**

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa oluşturun.

3. Aşağıdaki alt anahtarları, henüz **yoksa,** aşağıdaki tabloda gösterilen ilişkili değerlerle Dize Değeri olarak ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Bu Office için `Internet` varsayılan değere sahiptir `AuthenticodeRequired` ve `UntrustedSites` değerine `Disabled` sahiptir. Diğer tüm değerler `Internet` için varsayılan değeri `Enabled` vardır.

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Güven istemini program ClickOnce etkinleştirmek için

1. Visual Basic'da bir Visual Basic veya Visual C# konsol Visual Studio.

2. Düzenlemek için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Güvenlik ClickOnce istemini kısıtlama
 Kullanıcılardan güven kararı istenmeden önce, çözümlerin bilinen kimliğe sahip Authenticode sertifikaları ile imzalanacak şekilde güven istemini kısıtla.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri ClickOnce kullanarak güvenlik istemini kısıtlamak için

1. Kayıt defteri düzenleyicisini açın:

    1. Başlat **'a** ve ardından **Çalıştır'a tıklayın.**

    2. Aç **kutusuna yazın** ve `regedit` Tamam'a **tıklayın.**

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa oluşturun.

3. Aşağıdaki alt anahtarları, henüz **yoksa,** aşağıdaki tabloda gösterilen ilişkili değerlerle Dize Değeri olarak ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Güven istemini program ClickOnce kısıtlamak için

1. Visual Basic'da bir Visual Basic veya Visual C# konsol Visual Studio.

2. Düzenlemek için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="disable-the-clickonce-trust-prompt"></a>ClickOnce istemini devre dışı bırakma
 Güven istemini devre dışı bırakarak son kullanıcılara güvenlik ilkelerinde henüz güvenilmiyor olan çözümleri yükleme seçeneği verilmemiş olur.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini ClickOnce güvenlik istemini devre dışı bırakmak için

1. Kayıt defteri düzenleyicisini açın:

    1. Başlat **'a** ve ardından **Çalıştır'a tıklayın.**

    2. Aç **kutusuna yazın** ve `regedit` Tamam'a **tıklayın.**

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa oluşturun.

3. Aşağıdaki alt anahtarları, henüz **yoksa,** aşağıdaki tabloda gösterilen ilişkili değerlerle Dize Değeri olarak ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Güven istemini program ClickOnce devre dışı bırakmak için

1. Visual Basic'da bir Visual Basic veya Visual C# konsol Visual Studio.

2. Düzenlemek için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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
- [Nasıl yapabilirsiniz: ClickOnce ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl ClickOnce uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl ClickOnce uygulama için özel izinler ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl ClickOnce: ClickOnce uygulamanın hata ayıklaması](securing-clickonce-applications.md)
- [Nasıl kullanılır: İstemci uygulamaları için istemci bilgisayara güvenilir yayımcı ClickOnce ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl yapılanlar: Uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
