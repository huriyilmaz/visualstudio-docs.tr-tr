---
title: VSTO Eklentileri için kayıt defteri girdileri
description: Visual Studio kullanarak oluşturulan eklentilerini dağıtarak VSTO kayıt defteri girdileri kümesi oluşturma hakkında Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c613bb9642ad63a8df13dcf033e1618c79dd2c567d26f6dde62463aaec2a70d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267539"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO Eklentileri için kayıt defteri girdileri
  VSTO kullanarak oluşturulan eklentilerini dağıtırken belirli bir kayıt defteri girdisi kümesi Visual Studio. Bu kayıt defteri girdileri, uygulamanın Microsoft Office eklentisini bulmalarını ve yüklemesini VSTO bilgiler sağlar.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Projenizi derlemek Visual Studio kolayca çalıştırabilir ve eklentinin hata ayıklaması için bu kayıt defteri girdilerini geliştirme VSTO oluşturur. ClickOnce eklentinizi dağıtmak için VSTO kullanırsanız, kayıt defteri girişleri son kullanıcı bilgisayarda otomatik olarak oluşturulur. Windows Eklentinizi dağıtmak için VSTO Yükleyicisi kullanıyorsanız, son kullanıcı bilgisayarda kayıt defteri girdileri oluşturmak için InstallShield Limited Edition projesini yapılandırmanız gerekir.

 VSTO Eklentileri için yükleme işlemi sırasında kayıt defteri girişlerinin nasıl VSTO için [bkz. VSTO Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

> [!NOTE]
> Bu konu başlığında metin *eklenti kimliği,* eklentiniz için benzersiz bir kimliği VSTO temsil eder. Varsayılan olarak, kimlik, eklenti derlemenizin VSTO adıdır.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Geçerli VSTO ve tüm kullanıcılar için uygulama eklentilerini kaydetme
 Bir VSTO yüklemesi iki şekilde kaydedebilirsiniz:

- Yalnızca geçerli kullanıcı için (başka bir ifadeyle, yalnızca VSTO Eklenti yüklü olduğunda bilgisayarda oturum açmış olan kullanıcı tarafından kullanılabilir). Bu durumda, kayıt defteri girdileri **HKEY_CURRENT_USER.**

- Tüm kullanıcılar için (başka bir ifadeyle, bilgisayarda oturum açtığınız tüm kullanıcılar VSTO kullanabilir). Bu durumda, kayıt defteri girdileri **HKEY_LOCAL_MACHINE.**

  VSTO kullanarak oluştursanız tüm Visual Studio geçerli kullanıcı için kayded olabilir. Ancak VSTO eklentileri yalnızca belirli senaryolarda tüm kullanıcılar için kaydedebilirsiniz. Bu senaryolar, bilgisayarda Microsoft Office sürümüne ve VSTO dağıtıldıklarına bağlıdır.

### <a name="deployment-type"></a>Dağıtım türü
 ClickOnce eklentisini dağıtmak için VSTO kullanırsanız, VSTO Eklenti yalnızca geçerli kullanıcı için kayded olabilir. Bunun nedeni, ClickOnce yalnızca HKEY_CURRENT_USER **altında anahtarların oluşturulmasını desteklemesidir.** Bir bilgisayarda tüm kullanıcılara bir VSTO eklentisini kaydetmek için, Windows Yükleyicisi'VSTO dağıtmanız gerekir. Bu dağıtım türleri hakkında daha fazla bilgi için [bkz. Office](../vsto/deploying-an-office-solution-by-using-clickonce.md) kullanarak ClickOnce çözümü dağıtma ve Office Yükleyicisi'Windows [dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="registry-entries"></a>Kayıt defteri girdileri
 Gerekli VSTO kayıt defteri girdileri, yüklemenin geçerli kullanıcıya  veya  tüm kullanıcılara yönelik olup HKEY_CURRENT_USER veya **HKEY_LOCAL_MACHINE** kök olduğu aşağıdaki kayıt defteri anahtarlarında bulunur.

|Office Uygulama|Yapılandırma Yolu|
|------------------|------------------|
|Visio|*Root*\Software\Microsoft \\ *Visio*\Addins \\ *eklenti kimliği*|
|Tüm Diğer|*Root*\Software\Microsoft\Office \\ *Office uygulama adı*\Addins \\ *eklenti kimliği*|

> [!NOTE]
> Yükleyici 64 bit Windows'deki tüm kullanıcıları hedeflese, biri HKEY_LOCAL_MACHINE\Software\Microsoft'nin altında ve biri \\ **de HKEY_LOCAL_MACHINE\SoftwareWOW6432Node**\Microsoft hive altında olmak HKEY_LOCAL_MACHINE\Softwarekayıt defteri girdisi içerir. Bunun nedeni, kullanıcıların bilgisayarın 32 bit veya 64 bitlik sürümlerini Office mümkün olabilir.
>
>Yükleyici geçerli kullanıcıyı hedefleyebilse, yeni yol paylaşılırken WOW6432Node'a HKEY_CURRENT_USER\Software gerek yok.
>
>Daha fazla bilgi için lütfen [Kayıt Defterindeki 32 bit ve 64 bit Uygulama Verileri'ne bakın](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 Aşağıdaki tabloda, bu kayıt defteri anahtarı altındaki girişler liste almaktadır.

|Giriş|Tür|Değer|
|-----------|----------|-----------|
|**Açıklama**|REG_SZ|Gereklidir. Eklentinin kısa VSTO açıklaması.<br /><br /> Bu açıklama, kullanıcı VSTO uygulamanın Seçenekler iletişim kutusunun Eklentiler  bölmesindeki Eklentiyi  Microsoft Office görüntülenir.|
|**Friendlyname**|REG_SZ|Gereklidir. VSTO uygulamasında **COM** Eklentileri iletişim kutusunda görüntülenen eklentinin açıklayıcı Microsoft Office. Varsayılan değer, VSTO kimliğidir.|
|**Loadbehavior**|REG_DWORD|Gereklidir. Uygulamanın eklentiyi ne zaman yüklemeye VSTO eklentinin geçerli durumunu (yüklenen veya kaldırılan) VSTO belirten bir değer.<br /><br /> Varsayılan olarak, bu giriş 3 olarak ayarlanır ve bu da VSTO eklentinin başlangıçta yükleniyor olduğunu belirtir. Daha fazla bilgi için bkz. [LoadBehavior değerleri.](#LoadBehavior) **Not:**  Bir kullanıcı eklentiyi devre VSTO, bu eylem kayıt defteri kovanının **LoadBehavior** **değerini HKEY_CURRENT_USER** olur. Her kullanıcı için, HKEY_CURRENT_USER hive'daki **LoadBehavior** değerinin değeri, HKEY_LOCAL_MACHINE hive içinde tanımlanan varsayılan **LoadBehavior'HKEY_LOCAL_MACHINE** geçersiz kılar. |
|**Bildirim**|REG_SZ|Gereklidir. VSTO Eklenti için dağıtım bildiriminin tam yolu. Yol yerel bilgisayarda, ağ paylaşımında (UNC) veya Web sunucusunda (HTTP) bir konum olabilir.<br /><br /> Çözümü dağıtmak Windows Yükleyicisi kullanıyorsanız, bildirim yoluna **file:///** **önekini** eklemeniz gerekir. Ayrıca, dizeyi **vstolocal&#124;** (diğer bir&#124;ve  **ardından vstolocal)** bu yolun sonuna ekleniz gerekir. Bu, çözüm yükleme önbelleği yerine yükleme klasöründen ClickOnce sağlar. Daha fazla bilgi için [bkz. Office Yükleyicisi kullanarak bir Windows dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md) **Not:**  Geliştirme bilgisayarda VSTO eklentisini derlemek, Visual Studio kayıt defteri&#124;**vstolocal** dizesini otomatik olarak ekler.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Form bölgelerinin kayıt Outlook girdileri
 Outlook için VSTO Eklentisinde özel bir form bölgesi oluşturmanız Outlook. Bu girişler, form bölgesi tarafından destekleyen her ileti sınıfı için farklı bir kayıt defteri anahtarı altında oluşturulur. Bu kayıt defteri anahtarları Aşağıdaki konumdadır; *Kök,* **HKEY_CURRENT_USER** **veya** HKEY_LOCAL_MACHINE.

 *Root*\Software\Microsoft\Office\Outlook\FormRegions \\ *ileti sınıfı*

 Tüm kaynak eklentileri tarafından paylaşılan diğer kayıt VSTO gibi, Visual Studio projenizi derlemek için geliştirme bilgisayarda form bölgesi kayıt defteri girdilerini oluşturur. ClickOnce eklentinizi dağıtmak için VSTO kullanırsanız, kayıt defteri girişleri son kullanıcı bilgisayarda otomatik olarak oluşturulur. Windows Eklentinizi dağıtmak için VSTO Yükleyicisi kullanıyorsanız, son kullanıcı bilgisayarda kayıt defteri girdileri oluşturmak için InstallShield Limited Edition projesini yapılandırmanız gerekir.

 Form bölgesi kayıt defteri girdileri hakkında daha fazla bilgi için [bkz. Özel bir formda form bölgesi konumunu belirtme.](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form) Form bölgelerini oluşturma hakkında Outlook için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a> LoadBehavior değerleri
 *Root*\Software\Microsoft\Office uygulama adı \Addins eklenti kimliği anahtarı altındaki **LoadBehavior** girdisi, eklentinin çalışma zamanı davranışını belirten \\  \\  değerlerin bitwise VSTO içerir. En düşük sıralama biti (0 ve 1 değerleri), eklentinin VSTO yüklenmemiş veya yüklenmemiş olduğunu gösterir. Diğer bitler, uygulamanın eklentiyi ne zaman VSTO olduğunu gösteriyor.

 Genellikle, VSTO Eklenti son kullanıcı bilgisayarlarına yüklenirken **LoadBehavior** girdisi 0, 3 veya 16 (ondalık) olarak ayarlanır. Varsayılan olarak, Visual Studio veya yayımlarken VSTO eklentinizin **LoadBehavior** girdisini 3 olarak ayarlar.

 Aşağıdaki tabloda **LoadBehavior** girişinin tüm olası değerleri listelemektedir. Bu tablodaki bazı açıklamalar, eklentinin el VSTO program aracılığıyla yüklenmesine başvurur. Eklentiyi el VSTO yüklemek için, uygulamanın **COM** Eklentileri iletişim kutusunda VSTO'nin yanındaki onay kutusunu işaretleyin. Eklentiyi program VSTO yüklemek için, eklentiyi temsil eden nesnenin özelliğini true VSTO olarak <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> <xref:Microsoft.Office.Core.COMAddIn> **ayarlayın.**

|Değer (ondalık)|VSTO Eklenti durumu|VSTO Eklenti yükleme davranışı|Açıklama|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Kaldırıldı|Otomatik olarak yükleme|Uygulama, eklentiyi otomatik olarak VSTO denemez. Kullanıcı eklentiyi el ile VSTO deneyebilir veya VSTO eklenti program aracılığıyla yüklenebilir.<br /><br /> VSTO Eklenti başarıyla yüklenirse **LoadBehavior** değeri 0 kalır, ancak **COM** Eklentileri iletişim kutusundaki VSTO Eklentinin durumu, VSTO Eklentinin yükleniyor olduğunu belirtmek için güncelleştirilir.|
|1|Yüklü|Otomatik olarak yükleme|uygulama hiçbir durumda VSTO eklentisini otomatik olarak yüklemeyi denemez. kullanıcı VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> **COM eklentileri** iletişim kutusu, uygulama başladıktan sonra VSTO eklentisinin yüklendiğini belirtir, ancak el ile veya program aracılığıyla yükleninceye kadar VSTO eklentisi yüklenmez.<br /><br /> uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 0 olarak değişir ve uygulama kapandıktan sonra 0 ' da kalır.|
|2|Kaldırıldı|Başlangıçta yükle|uygulama VSTO eklentisini otomatik olarak yüklemeyi denemez. kullanıcı VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 3 olarak değişir ve uygulama kapandıktan sonra 3 ' te kalır.|
|3|Yüklü|Başlangıçta yükle|uygulama, uygulama başladığında VSTO eklentisini yüklemeye çalışır. bu, Visual Studio bir VSTO eklentisi oluştururken veya yayımladığınızda varsayılan değerdir.<br /><br /> uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 3 kalır. VSTO eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 2 olarak değişir ve uygulama kapandıktan sonra 2 ' de kalır.|
|8|Kaldırıldı|İsteğe bağlı yükleme|uygulama VSTO eklentisini otomatik olarak yüklemeyi denemez. kullanıcı VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> uygulama VSTO eklentisini başarıyla yüklerse, **LoadBehavior** değeri 9 olarak değişir.|
|9|Yüklü|İsteğe bağlı yükleme|VSTO eklentisi yalnızca uygulama için gerekli olduğunda, örneğin, bir kullanıcı, VSTO eklentisinin işlevlerini kullanan bir kullanıcı arabirimi öğesine tıkladığında (örneğin, şeritte özel bir düğme) yüklenecektir.<br /><br /> uygulama VSTO eklentisini başarılı bir şekilde yüklerse, **LoadBehavior** değeri 9 kalır, ancak **COM** eklentileri iletişim kutusunda VSTO eklentisinin durumu, VSTO eklentisinin o anda yüklü olduğunu gösterecek şekilde güncelleştirilir. VSTO eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 8 olarak değişir.|
|16|Yüklü|İlk kez yükle, sonra isteğe bağlı olarak yükle|VSTO eklentisinin isteğe bağlı olarak yüklenmesini istiyorsanız bu değeri ayarlayın. kullanıcı uygulamayı ilk kez çalıştırdığında, uygulama VSTO eklentisini yükler. kullanıcı uygulamayı bir dahaki sefer çalıştırdığında, uygulama VSTO eklentisi tarafından tanımlanan kullanıcı arabirimi öğelerini yükler, ancak kullanıcı VSTO eklentisi ile ilişkili bir kullanıcı arabirimi öğesine tıklayana kadar VSTO eklentisi yüklenmez.<br /><br /> uygulama VSTO eklentisini ilk kez başarıyla yüklediğinde, VSTO eklentisi yüklenirken **LoadBehavior** değeri 16 kalır. Uygulama kapandıktan sonra, **LoadBehavior** değeri 9 olarak değişir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Office çözümlerin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
 