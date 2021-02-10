---
title: 'Nasıl yapılır: ekleme listesi güvenliğini yapılandırma'
description: Son kullanıcılara, ekleme listesine bir güven kararı kaydederek Office çözümlerini yükleme seçeneği verilip verilmediğini denetlemek için ClickOnce güven istemi 'ni yapılandırın.
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
ms.workload:
- office
ms.openlocfilehash: ddbc74c00c1e1f74ce078586d624e2da4dbd8163
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954026"
---
# <a name="how-to-configure-inclusion-list-security"></a>Nasıl yapılır: ekleme listesi güvenliğini yapılandırma
  Yönetici izinleriniz varsa, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] son kullanıcılara, ekleme listesine bir güven kararı kaydederek Office çözümlerini yükleme seçeneği verilip verilmediğini denetlemek için güven istemi 'ni yapılandırabilirsiniz. Ekleme listeleri hakkında daha fazla bilgi için bkz. [ekleme listelerini kullanarak Office çözümlerine güvenme](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Beş bölgenin her birinde bulunan çözümler için aşağıdaki seçenekleri belirleyebilirsiniz:

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Güven Istemi anahtarını ve ekleme listesini etkinleştirin. Son kullanıcıların, herhangi bir sertifikayla imzalanmış Office çözümlerine güven izni vermesini sağlayabilirsiniz.

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Güven Istemi anahtarını ve ekleme listesini kısıtlayın. Son kullanıcıların yayımcıyı tanımlayan bir sertifikayla imzalanmış, ancak henüz güvenilmeyen Office çözümlerini yüklemesine izin verebilirsiniz.

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Güven Istemi anahtarını ve ekleme listesini devre dışı bırakın. Son kullanıcıların açıkça güvenilen bir sertifikayla imzalı olmayan herhangi bir Office çözümünü yüklemesini engelleyebilirsiniz.

## <a name="enable-the-inclusion-list"></a>Ekleme listesini etkinleştir
 Son kullanıcılara, bu bölgeden gelen herhangi bir Office çözümünü yükleme ve çalıştırma seçeneği ile sunulmasını istediğinizde, bir bölge için ekleme listesini etkinleştirin.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Kayıt defteri düzenleyicisini kullanarak ekleme listesini etkinleştirmek için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna **regedt32.exe** yazın ve ardından **Tamam**' a tıklayın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa, oluşturun.

3. Zaten mevcut değilse, ilişkili değerlerle aşağıdaki alt anahtarları **dize değeri** olarak ekleyin.

    |Dize değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**İnternet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Devre dışı**|
    |**Bilgisayarım**|**Etkin**|
    |**Yerel Intranet**|**Etkin**|
    |**TrustedSites**|**Etkin**|

     Varsayılan olarak, **Internet** **AuthenticodeRequired** değerine sahiptir ve **UntrustedSites** değeri **devre dışı bırakılır**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Ekleme listesini programlı bir şekilde etkinleştirmek için

1. Visual Basic veya Visual C# konsol uygulaması oluşturun.

2. Düzenlenmek üzere *program. vb* veya *program.cs* dosyasını açın ve aşağıdaki kodu ekleyin.

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

## <a name="restrict-the-inclusion-list"></a>Ekleme listesini kısıtla
 Ekleme listesini, kullanıcılardan bir güven kararı istenmeden önce bilinen kimliği olan Authenticode sertifikaları ile imzalanması gerekir.

### <a name="to-restrict-the-inclusion-list"></a>Ekleme listesini kısıtlamak için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna **regedt32.exe** yazın ve ardından **Tamam**' a tıklayın.

2. Aşağıdaki kayıt defteri anahtarını bulun:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Anahtar yoksa, oluşturun.

3. Zaten mevcut değilse, ilişkili değerlerle aşağıdaki alt anahtarları **dize değeri** olarak ekleyin.

    |Dize değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**UntrustedSites**|**Devre dışı**|
    |**İnternet**|**AuthenticodeRequired**|
    |**Bilgisayarım**|**AuthenticodeRequired**|
    |**Yerel Intranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Varsayılan olarak, **Internet** **AuthenticodeRequired** değerine sahiptir ve **UntrustedSites** değeri **devre dışı bırakılır**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Ekleme listesini programlı bir şekilde kısıtlamak için

1. Visual Basic veya Visual C# konsol uygulaması oluşturun.

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

## <a name="disable-the-inclusion-list"></a>Ekleme listesini devre dışı bırak
 Son kullanıcıların yalnızca güvenilir ve bilinen bir sertifikayla imzalanmış çözümler yükleyebilmesi için ekleme listesini devre dışı bırakabilirsiniz.

### <a name="to-disable-the-inclusion-list"></a>Ekleme listesini devre dışı bırakmak için

1. Kayıt defteri düzenleyicisini açın:

    1. **Başlat**' a ve ardından **Çalıştır**' a tıklayın.

    2. **Aç** kutusuna **regedt32.exe** yazın ve ardından **Tamam**' a tıklayın.

2. Zaten yoksa, aşağıdaki kayıt defteri anahtarını oluşturun:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

3. Zaten mevcut değilse, ilişkili değerlerle aşağıdaki alt anahtarları **dize değeri** olarak ekleyin.

    |Dize değeri alt anahtarı|Değer|
    |-------------------------|-----------|
    |**UntrustedSites**|**Devre dışı**|
    |**İnternet**|**Devre dışı**|
    |**Bilgisayarım**|**Devre dışı**|
    |**Yerel Intranet**|**Devre dışı**|
    |**TrustedSites**|**Devre dışı**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Ekleme listesini programlı olarak devre dışı bırakmak için

1. Visual Basic veya Visual C# konsol uygulaması oluşturun.

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
- [Ekleme listelerini kullanarak Office çözümlerine güvenme](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
