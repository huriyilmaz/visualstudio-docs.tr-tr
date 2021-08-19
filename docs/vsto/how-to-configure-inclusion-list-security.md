---
title: 'Nasıl yapılandırılır: Ekleme listesi güvenliğini yapılandırma'
description: Son ClickOnce bir güven kararı ekleme listesine kaydederek son kullanıcıların Office yükleme seçeneğine sahip olup olmadığını kontrol etmek için güvenlik güven istemini yapılandırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: adde40770aad2d665ad482b72189abda2d6d4176
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148187"
---
# <a name="how-to-configure-inclusion-list-security"></a>Nasıl yapılandırılır: Ekleme listesi güvenliğini yapılandırma
  Yönetici izinlerine sahipseniz, bir güven kararını dahil etme listesine kaydederek son kullanıcılara Office çözümü yükleme seçeneği olup olmadığını kontrol etmek için güven [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] istemini yapılandırabilirsiniz. Dahil etme listeleri hakkında bilgi için [bkz. Dahil etme Office çözümlerine güven.](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Beş bölgenin her birsinde yer alan çözümler için aşağıdaki seçenekleri ayarlayın:

- Güven [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] İstemi Anahtarını ve ekleme listesini etkinleştirin. Son kullanıcıların herhangi bir sertifikayla imzalanan Office çözümlere güven vermesine izin veebilirsiniz.

- Güven [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] İstemi Anahtarını ve ekleme listesini kısıtla. Son kullanıcıların, yayımcıyı tanımlayan Office ile imzalanmış ancak henüz güvenilir bir çözüme sahip bir çözüm yüklemesine izin veebilirsiniz.

- Güven [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] İstemi Anahtarını ve ekleme listesini devre dışı bırakma. Son kullanıcıların açıkça güvenilen bir sertifikayla Office bir çözüm yüklemesini önleyebilirsiniz.

## <a name="enable-the-inclusion-list"></a>Ekleme listesini etkinleştirme
 Son kullanıcılara bu bölgeden gelen herhangi bir çözüm yükleme ve çalıştırma seçeneği Office bir bölge için ekleme listesini etkinleştirin.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ekleme listesini etkinleştirmek için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat'a** ve ardından Çalıştır'a **tıklayın.**

    2. Aç kutusuna **yazın** regedt32.exe **tamam'a** **tıklayın.**

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa oluşturun.

3. Aşağıdaki alt anahtarları, henüz **yoksa dize** değeri olarak ilişkili değerlerle birlikte ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**İnternet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Devre dışı**|
    |**Bilgisayarım**|**Etkin**|
    |**Localıntranet**|**Etkin**|
    |**TrustedSites**|**Etkin**|

     İnternet varsayılan **olarak** **AuthenticodeRequired,** **UntrustedSites** ise Disabled değerine **sahip olur.**

### <a name="to-enable-the-inclusion-list-programmatically"></a>Dahil etme listesini program aracılığıyla etkinleştirmek için

1. Bir Visual Basic veya Visual C# konsol uygulaması oluşturun.

2. Düzenlemek için *Program.vb* veya *Program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
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

## <a name="restrict-the-inclusion-list"></a>Ekleme listesini kısıtlama
 Kullanıcılardan güven kararı istenmeden önce çözümlerin bilinen kimliğe sahip Authenticode sertifikaları ile imzalanacak şekilde dahil etme listesini kısıtla.

### <a name="to-restrict-the-inclusion-list"></a>Ekleme listesini kısıtlamak için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat'a** ve ardından Çalıştır'a **tıklayın.**

    2. Aç kutusuna **yazın** regedt32.exe **tamam'a** **tıklayın.**

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa oluşturun.

3. Aşağıdaki alt anahtarları, henüz **yoksa dize** değeri olarak ilişkili değerlerle birlikte ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**UntrustedSites**|**Devre dışı**|
    |**İnternet**|**AuthenticodeRequired**|
    |**Bilgisayarım**|**AuthenticodeRequired**|
    |**Localıntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     İnternet varsayılan **olarak** **AuthenticodeRequired,** **UntrustedSites** ise Disabled değerine **sahip olur.**

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Dahil etme listesini program aracılığıyla kısıtlamak için

1. Bir Visual Basic veya Visual C# konsol uygulaması oluşturun.

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

## <a name="disable-the-inclusion-list"></a>Ekleme listesini devre dışı bırakma
 Son kullanıcıların yalnızca güvenilen ve bilinen bir sertifikayla imzalanmış çözümleri yükley yüklemesi için dahil etme listesini devre dışı ekleyebilirsiniz.

### <a name="to-disable-the-inclusion-list"></a>Ekleme listesini devre dışı bırakmak için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat'a** ve ardından Çalıştır'a **tıklayın.**

    2. Aç kutusuna **yazın** regedt32.exe **tamam'a** **tıklayın.**

2. Henüz yoksa aşağıdaki kayıt defteri anahtarını oluşturun:

     **\\\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT. NETFramework\Security\TrustManager\PromptingLevel**

3. Aşağıdaki alt anahtarları, henüz **yoksa dize** değeri olarak ilişkili değerlerle birlikte ekleyin.

    |Dize Değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**UntrustedSites**|**Devre dışı**|
    |**İnternet**|**Devre dışı**|
    |**Bilgisayarım**|**Devre dışı**|
    |**Localıntranet**|**Devre dışı**|
    |**TrustedSites**|**Devre dışı**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Dahil etme listesini program aracılığıyla devre dışı bırakmak için

1. Bir Visual Basic veya Visual C# konsol uygulaması oluşturun.

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
- [Dahil Office kullanarak çözüme güvenin](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
