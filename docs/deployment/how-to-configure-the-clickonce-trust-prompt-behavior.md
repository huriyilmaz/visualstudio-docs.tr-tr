---
title: ClickOnce güven Istemi davranışını yapılandırma | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7417f9cdce21dc09aeaf306b55834ad7d3a125a6
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382555"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma
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

## <a name="enable-the-clickonce-trust-prompt"></a>ClickOnce güven istemi 'ni etkinleştir
 Son kullanıcılara, bu bölgeden gelen herhangi bir ClickOnce uygulamasını yükleme ve çalıştırma seçeneği ile sunulmasını istediğinizde, bir bölge için güven istemi 'ni etkinleştirin.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni etkinleştirmek için

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna yazın `regedit` ve ardından **Tamam**' a tıklayın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

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

2. Düzenlenmek üzere *program. vb* veya *program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>ClickOnce güven istemi 'ni kısıtla
 Güven istemi 'ni, kullanıcılardan bir güven kararı istenmeden önce bilinen kimliği olan Authenticode sertifikaları ile imzalanması gerekir.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni kısıtlamak için

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna yazın `regedit` ve ardından **Tamam**' a tıklayın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

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

2. Düzenlenmek üzere *program. vb* veya *program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="disable-the-clickonce-trust-prompt"></a>ClickOnce güven istemi 'ni devre dışı bırak
 Güven istemi 'ni devre dışı bırakarak, son kullanıcılara güvenlik ilkesinde henüz güvenilmeyen çözümleri yüklemek için seçenek verilmez.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ClickOnce güven istemi 'ni devre dışı bırakmak için

1. Kayıt defteri düzenleyicisini açın: 

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna yazın `regedit` ve ardından **Tamam**' a tıklayın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

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

2. Düzenlenmek üzere *program. vb* veya *program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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
- [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl yapılır: kısıtlanmış izinlerle ClickOnce uygulamasında hata ayıklama](securing-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
