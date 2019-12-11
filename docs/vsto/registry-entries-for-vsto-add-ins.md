---
title: VSTO eklentileri için kayıt defteri girişleri
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 464820258e5c20474d74f92eb108344deccc49f1
ms.sourcegitcommit: 0a8855572c6c88f4b2ece232c04aa124fbd9cec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955055"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO eklentileri için kayıt defteri girişleri
  Visual Studio kullanılarak oluşturulan VSTO Eklentilerini dağıtırken belirli bir kayıt defteri girişi kümesi oluşturmanız gerekir. Bu kayıt defteri girdileri, Microsoft Office uygulamasının VSTO eklentisini bulmasını ve yüklemesini sağlayan bilgiler sağlar.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Projenizi yapılandırdığınızda, Visual Studio bu kayıt defteri girdilerini geliştirme bilgisayarında oluşturur, böylece VSTO eklentisini kolayca çalıştırıp hata ayıklaması yapabilirsiniz. VSTO eklentisini dağıtmak için ClickOnce kullanırsanız, kayıt defteri girdileri son kullanıcı bilgisayarında otomatik olarak oluşturulur. VSTO eklentisini dağıtmak için Windows Installer kullanıyorsanız, InstallShield Limited Edition projesini Son Kullanıcı bilgisayarında kayıt defteri girişlerini oluşturacak şekilde yapılandırmanız gerekir.

 VSTO eklentileri için yükleme işlemi sırasında kayıt girdilerinin nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> In this topic, the text *add-in ID* represents a unique ID for your VSTO Add-in. By default, the ID is the name of your VSTO Add-in assembly.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Register VSTO Add-ins for the current user vs. all users
 When a VSTO Add-in is installed, it can be registered in two ways:

- For the current user only (that is, it is available only to the user that is logged on to the computer when the VSTO Add-in is installed). In this case, the registry entries are created under the **HKEY_CURRENT_USER**.

- For all users (that is, any user that logs on to the computer can use the VSTO Add-in). In this case, the registry entries are created under **HKEY_LOCAL_MACHINE**.

  All VSTO Add-ins that you create by using Visual Studio can be registered for the current user. However, VSTO Add-ins can be registered for all users only in certain scenarios. These scenarios depend on the version of Microsoft Office on the computer and how the VSTO Add-in was deployed.

### <a name="deployment-type"></a>Dağıtım türü
 If you use ClickOnce to deploy a VSTO Add-in, the VSTO Add-in can be registered only for the current user. This is because ClickOnce only supports creating keys under **HKEY_CURRENT_USER**. If you want to register a VSTO Add-in to all users on a computer, you must use Windows Installer to deploy the VSTO Add-in. For more information about these deployment types, see [Deploy an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) and [Deploy an Office solution by using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Kayıt defteri girdileri
 The required VSTO Add-in registry entries are located under the following registry keys where *Root* is **HKEY_CURRENT_USER** or **HKEY_LOCAL_MACHINE** depending if the installation is for the current user or all users.

|Office Application|Configuration Path|
|------------------|------------------|
|Visio|*Root*\Software\Microsoft\\*Visio*\Addins\\*add-in ID*|
|All Other|*Root*\Software\Microsoft\Office\\*Office application name*\Addins\\*add-in ID*|

> [!NOTE]
> If the installer is targeting all users on 64-bit Windows, it is recommended that it includes two registry entries, one under the HKEY_LOCAL_MACHINE\Software\Microsoft and one under the HKEY_LOCAL_MACHINE\Software\\**WOW6432Node**\Microsoft hive. This is because it's possible for users to use either 32-bit or 64-bit versions of Office on the computer.
>
>If the Installer is targeting the current user, it does not need to install to the WOW6432Node because the HKEY_CURRENT_USER\Software path is shared.
>
>For more information please see [32-bit and 64-bit Application Data in the Registry](https://docs.microsoft.com/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 The following table lists the entries under this registry key.

|Giriş|Tür|Değer|
|-----------|----------|-----------|
|**Açıklama**|REG_SZ|Gerekli. A brief description of the VSTO Add-in.<br /><br /> This description is displayed when the user selects the VSTO Add-in in the **Add-Ins** pane of the **Options** dialog box in the Microsoft Office application.|
|**FriendlyName**|REG_SZ|Gerekli. A descriptive name of the VSTO Add-in that is displayed in the **COM Add-Ins** dialog box in the Microsoft Office application. The default value is the VSTO Add-in ID.|
|**LoadBehavior**|REG_DWORD|Gerekli. A value that specifies when the application attempts to load the VSTO Add-in and the current state of the VSTO Add-in (loaded or unloaded).<br /><br /> By default, this entry is set to 3, which specifies that the VSTO Add-in is loaded at startup. For more information, see [LoadBehavior values](#LoadBehavior). **Note:**  If a user disables the VSTO Add-in, that action modifies **LoadBehavior** value in the **HKEY_CURRENT_USER** registry hive. For each user, the value of the **LoadBehavior** value in the HKEY_CURRENT_USER hive overrides the default **LoadBehavior** defined in the **HKEY_LOCAL_MACHINE** hive.|
|**Bildirimi**|REG_SZ|Gerekli. The full path of the deployment manifest for the VSTO Add-in. The path can be a location on the local computer, a network share (UNC), or a Web server (HTTP).<br /><br /> If you use Windows Installer to deploy the solution, you must add the prefix **file:///** to the **manifest** path. You must also append the string **&#124;vstolocal** (that is, the pipe character **&#124;** followed by **vstolocal**) to the end of this path. This ensures that your solution is loaded from the installation folder, rather than the ClickOnce cache. Daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Note:**  Geliştirme bilgisayarında bir VSTO eklentisi yapılandırdığınızda, Visual Studio bu kayıt defteri girişine  **&#124;vstolocal** dizesini otomatik olarak ekler.|

### <a name="OutlookEntries"></a>Outlook form bölgeleri için kayıt defteri girişleri
 Outlook için VSTO eklentisi içinde özel bir form bölgesi oluşturursanız, form bölgesini Outlook 'a kaydetmek için ek kayıt defteri girişleri kullanılır. Bu girdiler, form bölgesinin desteklediği her ileti sınıfı için farklı bir kayıt defteri anahtarı altında oluşturulur. Bu kayıt defteri anahtarları, *kökün* **HKEY_CURRENT_USER** veya **HKEY_LOCAL_MACHINE**olduğu aşağıdaki konumdadır.

 *Kök*\Software\microsoft\office\outlook\formregion\\*ileti sınıfı*

 Tüm VSTO eklentileri tarafından paylaşılan diğer kayıt defteri girdileri gibi, Visual Studio, projenizi oluştururken geliştirme bilgisayarında form bölgesi kayıt defteri girişlerini oluşturur. VSTO eklentisini dağıtmak için ClickOnce kullanırsanız, kayıt defteri girdileri son kullanıcı bilgisayarında otomatik olarak oluşturulur. VSTO eklentisini dağıtmak için Windows Installer kullanıyorsanız, InstallShield Limited Edition projesini Son Kullanıcı bilgisayarında kayıt defteri girişlerini oluşturacak şekilde yapılandırmanız gerekir.

 Form bölgesi kayıt defteri girişleri hakkında daha fazla bilgi için bkz. [özel bir formda form bölgesinin konumunu belirtme](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Outlook form bölgeleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

## <a name="LoadBehavior"></a>LoadBehavior değerleri
 *Kök*\software\microsoft\office\\*uygulama adı*\addıns\\*Add-In ID* anahtarı altındaki **LoadBehavior** girişi, VSTO eklentisinin çalışma süresi davranışını belirten bit düzeyinde bir değer birleşimini içerir. En düşük sıra biti (değerler 0 ve 1) VSTO eklentisinin Şu anda yüklü olup olmadığını belirtir. Diğer bitler, uygulamanın VSTO eklentisini yükleme girişiminde bulunduğunu gösterir.

 Genellikle, bir VSTO eklentisi son kullanıcı bilgisayarlarına yüklendiğinde, **LoadBehavior** girişinin 0, 3 veya 16 (ondalık olarak) olarak ayarlanması amaçlanmıştır. Varsayılan olarak, Visual Studio, VSTO eklentisinin, derleme veya yayımladığınızda 3 ' e yönelik **LoadBehavior** girişini ayarlar.

 Aşağıdaki tabloda, **LoadBehavior** girişinin tüm olası değerleri listelenmektedir. Bu tablodaki bazı açıklamalar, VSTO eklentisinin el ile veya program aracılığıyla yüklenmesine başvurur. VSTO eklentisini el ile yüklemek için, uygulamadaki **com eklentileri** ILETIŞIM kutusunda VSTO eklentisinin yanındaki onay kutusunu işaretleyin. Bir VSTO eklentisini programlı olarak yüklemek için, VSTO eklentisini temsil eden <xref:Microsoft.Office.Core.COMAddIn> nesnesinin <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> özelliğini **true**olarak ayarlayın.

|Değer (ondalık)|VSTO eklentisi durumu|VSTO eklenti yükleme davranışı|Açıklama|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Kaldırıldı|Otomatik olarak yükleme|Uygulama, VSTO eklentisini otomatik olarak yüklemeyi denemez. Kullanıcı, VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> VSTO eklentisi başarıyla yüklenmişse, **LoadBehavior** değeri 0 kalır, ancak **com EkLENTILERI** iletişim kutusundaki VSTO eklentisinin durumu, VSTO eklentisinin yüklendiğini belirtecek şekilde güncelleştirilir...|
|1\.|Yüklü|Otomatik olarak yükleme|Uygulama, VSTO eklentisini otomatik olarak yüklemeyi denemez. Kullanıcı, VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> **Com eklentileri** iletişim kutusu, VSTO eklentisinin uygulama başladıktan sonra yüklendiğini GÖSTERIYORSA, VSTO eklentisi el ile veya program aracılığıyla yükleninceye kadar yüklenmez.<br /><br /> Uygulama VSTO eklentisini başarılı bir şekilde yüklerse, **LoadBehavior** değeri 0 olarak değişir ve uygulama kapandıktan sonra 0 ' da kalır.|
|2|Kaldırıldı|Başlangıçta yükle|Uygulama, VSTO eklentisini otomatik olarak yüklemeyi denemez. Kullanıcı, VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> Uygulama VSTO eklentisini başarılı bir şekilde yüklerse, **LoadBehavior** değeri 3 olarak değişir ve uygulama kapandıktan sonra 3 ' te kalır.|
|3|Yüklü|Başlangıçta yükle|Uygulama, uygulama başladığında VSTO eklentisini yüklemeye çalışır. Bu, Visual Studio 'da bir VSTO eklentisi oluşturduğunuzda veya yayımladığınızda varsayılan değerdir.<br /><br /> Uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 3 kalır. VSTO eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 2 olarak değişir ve uygulama kapandıktan sonra 2 ' de kalır.|
|8|Kaldırıldı|İsteğe bağlı yükleme|Uygulama, VSTO eklentisini otomatik olarak yüklemeyi denemez. Kullanıcı, VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> Uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 9 olarak değişir.|
|9|Yüklü|İsteğe bağlı yükleme|VSTO eklentisi yalnızca uygulama için gerekli olduğunda, örneğin, bir kullanıcının VSTO eklentisinin işlevselliğini kullanan bir kullanıcı ARABIRIMI öğesine tıkladığı durumlarda (örneğin, şeritte özel bir düğme) yüklenir.<br /><br /> Uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 9 kalır, ancak **com EkLENTILERI** iletişim kutusundaki VSTO eklentisinin durumu, VSTO eklentisinin Şu anda yüklü olduğunu gösterecek şekilde güncelleştirilir. VSTO eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 8 olarak değişir.|
|16|Yüklü|İlk kez yükle, sonra isteğe bağlı olarak yükle|VSTO eklentisinin isteğe bağlı olarak yüklenmesini istiyorsanız bu değeri ayarlayın. Kullanıcı uygulamayı ilk kez çalıştırdığında, uygulama VSTO eklentisini yükler. Kullanıcı uygulamayı bir dahaki sefer çalıştırdığında, uygulama, VSTO eklentisi tarafından tanımlanan kullanıcı ARABIRIMI öğelerini yükler, ancak kullanıcı VSTO eklentisi ile ilişkili bir kullanıcı ARABIRIMI öğesini tıklayana kadar VSTO eklentisi yüklenmez.<br /><br /> Uygulama VSTO eklentisini ilk kez başarıyla yüklediğinde, VSTO eklentisi yüklenirken **LoadBehavior** değeri 16 kalır. Uygulama kapandıktan sonra, **LoadBehavior** değeri 9 olarak değişir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
