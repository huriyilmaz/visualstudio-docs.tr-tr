---
title: VSTO eklentileri için kayıt defteri girişleri
description: Visual Studio kullanılarak oluşturulan VSTO eklentileri dağıtırken belirli bir kayıt defteri girişi kümesi oluşturmayı öğrenin.
ms.custom: 'SEO-VS-2020, devdivchpfy22'
ms.date: 01/27/2022
ms.topic: conceptual
dev_langs:
  - VB
  - CSharp
helpviewer_keywords:
  - LoadBehavior entry
  - 'add-ins [Office development in Visual Studio], registry entries'
  - 'registry keys [Office development in Visual Studio]'
  - 'application-level add-ins [Office development in Visual Studio], registry entries'
  - 'registry entries [Office development in Visual Studio]'
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
  - office
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO eklentileri için kayıt defteri girişleri
  Visual Studio kullanılarak oluşturulan VSTO eklentileri dağıtırken belirli bir kayıt defteri girişleri kümesi oluşturmanız gerekir. bu kayıt defteri girdileri, Microsoft Office uygulamasının VSTO eklentisini bulmasını ve yüklemesini sağlayan bilgiler sağlar.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 projenizi oluşturduğunuzda Visual Studio geliştirme bilgisayarında bu kayıt defteri girişlerini oluşturur. bu, VSTO eklentisini kolayca çalıştırmanıza ve hata ayıklamanıza yardımcı olur. VSTO eklentiyi dağıtmak için ClickOnce kullanarak, kayıt defteri girdileri son kullanıcı bilgisayarında otomatik olarak oluşturulur. 

Windows Installer kullanarak VSTO çözümünün nasıl dağıtılacağı hakkında daha fazla bilgi için bkz. [Windows Installer kullanarak VSTO çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 VSTO eklentileri için yükleme işlemi sırasında kayıt girdilerinin nasıl kullanıldığı hakkında daha fazla bilgi için, bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> bu konuda, metin *eklentisi kimliği* , VSTO eklentisi için benzersiz bir kimliği temsil eder. varsayılan olarak, kimlik VSTO eklenti derlemelerinizin adıdır.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>geçerli kullanıcı ve tüm kullanıcılar için VSTO eklentilerini kaydet
 bir VSTO eklentisi yüklendiğinde, bu iki şekilde kaydedilebilir:

- yalnızca geçerli kullanıcı için (VSTO eklentisi yalnızca eklenti yüklendiğinde bilgisayarda oturum açan kullanıcı için kullanılabilir). Bu durumda, kayıt defteri girdileri **HKEY_CURRENT_USER** altında oluşturulur.

- tüm kullanıcılar için (yani, bilgisayarda oturum açan tüm kullanıcılar VSTO eklentisini kullanabilir). Bu durumda, kayıt defteri girdileri **HKEY_LOCAL_MACHINE** altında oluşturulur.

  Visual Studio kullanarak oluşturduğunuz tüm VSTO eklentileri geçerli kullanıcı için kaydedilebilir. ancak, VSTO eklentiler yalnızca belirli senaryolarda tüm kullanıcılar için kaydedilebilir. bu senaryolar bilgisayardaki Microsoft Office sürümüne ve VSTO eklentisinin nasıl dağıtıldığına bağlıdır.

### <a name="deployment-type"></a>Dağıtım türü
 VSTO eklentisini dağıtmak için ClickOnce kullanıyorsanız, VSTO eklentisi yalnızca geçerli kullanıcı için kaydedilebilir. bunun nedeni, ClickOnce yalnızca **HKEY_CURRENT_USER** altında anahtar oluşturulmasını destekler. bir bilgisayardaki tüm kullanıcılara bir VSTO eklentisi kaydetmek istiyorsanız VSTO eklentisini dağıtmak için Windows Installer kullanmalısınız. bu dağıtım türleri hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md) ve [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Kayıt defteri girdileri
 gerekli VSTO eklentisi kayıt defteri girdileri, *kökün* **HKEY_CURRENT_USER** veya yükleme geçerli kullanıcı veya tüm kullanıcılar için olup olmadığı **HKEY_LOCAL_MACHINE** bağlı olarak, aşağıdaki kayıt defteri anahtarlarının altında bulunur.

|Office uygulaması|Yapılandırma yolu|
|------------------|------------------|
|Visio|*kök*\software\microsoft \\ *Visio*\addıns \\ *eklenti kimliği*|
|Diğer tüm|*Root*\software\microsoft\ Office \\ *Office uygulama adı*\addıns \\ *eklenti kimliği*|

> [!NOTE]
> Yükleyici, 64 bitlik Windows tüm kullanıcıları hedefliyorsanız, biri HKEY_LOCAL_MACHINE\Software\Microsoft ve biri HKEY_LOCAL_MACHINE\Software\\ **Wow6432Node**\Microsoft Hive altında olmak üzere iki kayıt defteri girişi de içermesi önerilir. bunun nedeni, kullanıcıların bilgisayarda Office 32-bit ya da 64-bit sürümlerini kullanması olasıdır.
>
>Yükleyici geçerli kullanıcıyı hedefliyorsanız, HKEY_CURRENT_USER\Software yolu paylaşıldığından, WOW6432Node 'e yüklenmesi gerekmez.
>
>Daha fazla bilgi için bkz. [kayıt defterindeki 32-bit ve 64 bit uygulama verileri](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry).

 Aşağıdaki tabloda bu kayıt defteri anahtarı altındaki girdiler listelenmektedir.

|Giriş|Tür|Değer|
|-----------|----------|-----------|
|**Açıklama**|REG_SZ|Gereklidir. VSTO eklentisinin kısa bir açıklaması.<br /><br /> bu açıklama, kullanıcı Microsoft Office uygulamasındaki **seçenekler** iletişim kutusunun **eklentiler** bölmesinde VSTO eklentisini seçtiğinde görüntülenir.|
|**FriendlyName**|REG_SZ|Gereklidir. Microsoft Office uygulamasındaki **COM eklentileri** iletişim kutusunda görüntülenen VSTO eklentisinin açıklayıcı bir adı. varsayılan değer VSTO eklentisi kimliğidir.|
|**LoadBehavior**|REG_DWORD|Gereklidir. uygulamanın, VSTO eklentisinin (yüklenen veya yüklenmeyen) VSTO eklentisini ve geçerli durumunu ne zaman yüklemeye çalıştığında belirten bir değer.<br /><br /> bu giriş, varsayılan olarak, VSTO eklentisinin başlangıçta yüklendiğini belirten 3 olarak ayarlanır. Daha fazla bilgi için bkz. [LoadBehavior değerleri](#LoadBehavior).<br /><br />**Note:**  bir kullanıcı VSTO eklentisini devre dışı bırakırsa, bu eylem **HKEY_CURRENT_USER** kayıt hive içindeki **LoadBehavior** değerini değiştirir. Her bir kullanıcı için, HKEY_CURRENT_USER Hive içindeki **LoadBehavior** değeri değeri **HKEY_LOCAL_MACHINE** Hive içinde tanımlanan varsayılan **LoadBehavior** 'yi geçersiz kılar.|
|**Bildirim**|REG_SZ|Gereklidir. VSTO eklentisi için dağıtım bildiriminin tam yolu. Yol, yerel bilgisayarda, bir ağ paylaşımında (UNC) veya bir Web sunucusu 'nda (HTTP) bir konum olabilir.<br /><br /> çözümü dağıtmak için Windows Installer kullanırsanız, **bildirim** yoluna **file:///** önekini eklemeniz gerekir. Ayrıca, bu yolun sonuna **vstolocal** (diğer bir deyişle, **vstolocal** **&#124;** kanal karakteri)&#124;dizesini de eklemeniz gerekir. bu, çözümünüzün ClickOnce önbelleği yerine yükleme klasöründen yüklenmesini sağlar. daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).<br /><br />**Note:**  geliştirme bilgisayarında bir VSTO eklentisi oluşturduğunuzda Visual Studio, bu kayıt defteri girişine **&#124;vstolocal** dizesini otomatik olarak ekler.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Outlook form bölgeleri için kayıt defteri girişleri
 Outlook için bir VSTO eklentisi içinde özel form bölgesi oluşturursanız, form bölgesini Outlook kaydetmek için ek kayıt defteri girişleri kullanılır. Bu girdiler, form bölgesinin desteklediği her ileti sınıfı için farklı bir kayıt defteri anahtarı altında oluşturulur. Bu kayıt defteri anahtarları, *kökün* **HKEY_CURRENT_USER** veya **HKEY_LOCAL_MACHINE** olduğu aşağıdaki konumdadır.

 *kök*\software\microsoft\ Office \ Outlook \formregion \\ *ileti sınıfı*

 tüm VSTO eklentileri tarafından paylaşılan diğer kayıt defteri girdileri gibi, Visual Studio projenizi oluştururken geliştirme bilgisayarında form bölgesi kayıt defteri girişlerini oluşturur. VSTO eklentiyi dağıtmak için ClickOnce kullanarak, kayıt defteri girdileri son kullanıcı bilgisayarında otomatik olarak oluşturulur. VSTO eklentiyi dağıtmak için Windows Installer kullandığınızda, son kullanıcı bilgisayarında kayıt defteri girişlerini oluşturmak için ınstallshield Limited Edition projesini yapılandırmanız gerekir.

 Form bölgesi kayıt defteri girişleri hakkında daha fazla bilgi için bkz. [özel bir formda form bölgesinin konumunu belirtme](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Outlook form bölgeleri hakkında daha fazla bilgi için bkz. [Create Outlook form region](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a> LoadBehavior değerleri
 *kök*\software\microsoft\ Office \\ *application name*\addıns \\ *eklenti ıd* anahtarının altındaki **LoadBehavior** girişi, VSTO eklentisinin çalışma süresi davranışını belirten bit düzeyinde bir değer birleşimi içerir. en düşük sıra biti (değerler 0 ve 1), VSTO eklentisinin şu anda yüklü olup olmadığını belirtir. diğer bitler, uygulamanın VSTO eklentisini yükleme girişiminde bulunduğunu gösterir.

 genellikle, bir VSTO eklentisi son kullanıcı bilgisayarlarına yüklendiğinde, **LoadBehavior** girişi 0, 3 veya 16 (ondalık olarak) olarak ayarlanmalıdır. varsayılan olarak, Visual Studio VSTO eklentisinin **LoadBehavior** girişini, oluştururken veya yayımladığınızda 3 ' e ayarlar.

 Aşağıdaki tabloda, **LoadBehavior** girişinin tüm olası değerleri listelenmektedir. bu tablodaki bazı açıklamalar, el ile veya program aracılığıyla VSTO bir eklenti yüklemeye başvurur. VSTO bir eklentiyi el ile yüklemek için, uygulamadaki **COM eklentileri** iletişim kutusunda VSTO eklentisinin yanındaki onay kutusunu işaretleyin. programlı olarak bir VSTO eklentisi yüklemek için, VSTO eklentisini temsil eden nesnenin özelliğini <xref:Microsoft.Office.Core.COMAddIn> **true** olarak ayarlayın <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> .

|Değer (ondalık)|VSTO eklentisi durumu|VSTO eklentisi yükleme davranışı|Açıklama|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Kaldırıldı|Otomatik olarak yükleme|uygulama hiçbir durumda VSTO eklentisini otomatik olarak yüklemeyi denemez. kullanıcı VSTO eklentisini el ile yüklemeyi deneyebilir veya VSTO eklentisi programlı bir şekilde yüklenebilir.<br /><br /> VSTO eklentisi başarıyla yüklenmişse, **LoadBehavior** değeri 0 kalır, ancak **COM** eklentileri iletişim kutusundaki VSTO eklentisinin durumu, VSTO eklentisinin yüklendiğini belirtecek şekilde güncelleştirilir).|
|1|Yüklü|Otomatik olarak yüklenme|Uygulama hiçbir zaman eklentiyi otomatik VSTO yüklemez. Kullanıcı eklentiyi el ile VSTO deneyebilir veya VSTO eklenti program aracılığıyla yüklenebilir.<br /><br /> **COM Eklentileri iletişim** kutusu uygulama başladıktan sonra VSTO Eklentinin yükleniyor olduğunu gösteriyor olsa da, VSTO Eklenti el ile veya program aracılığıyla yüklenene kadar yüklenmez.<br /><br /> Uygulama eklentiyi başarıyla yüklerse VSTO **LoadBehavior** değeri 0 olarak değişir ve uygulama kapatıldıktan sonra 0'da kalır.|
|2|Kaldırıldı|Başlangıçta yükleme|Uygulama, eklentiyi otomatik olarak VSTO denemez. Kullanıcı eklentiyi el ile VSTO deneyebilir veya VSTO eklenti program aracılığıyla yüklenebilir.<br /><br /> Uygulama eklentiyi başarıyla yüklerse VSTO **LoadBehavior** değeri 3 olarak değişir ve uygulama kapatıldıktan sonra 3'te kalır.|
|3|Yüklü|Başlangıçta yükleme|Uygulama, uygulama başlatıldığında VSTO eklentiyi yüklemeye çalışır. Bu, bir eklentiyi derlemek veya yayımlamak için VSTO varsayılan değerdir Visual Studio.<br /><br /> Uygulama eklentiyi başarıyla VSTO **LoadBehavior** değeri 3 olarak kalır. VSTO Eklentisini yüklerken hata oluşursa **, LoadBehavior** değeri 2 olarak değişir ve uygulama kapatıldıktan sonra 2'de kalır.|
|8|Kaldırıldı|isteğe bağlı yükleme|Uygulama, eklentiyi otomatik olarak VSTO denemez. Kullanıcı eklentiyi el ile VSTO deneyebilir veya VSTO eklenti program aracılığıyla yüklenebilir.<br /><br /> Uygulama eklentiyi başarıyla yüklerse VSTO **LoadBehavior** değeri 9 olarak değişir.|
|9|Yüklü|isteğe bağlı yükleme|VSTO Eklenti yalnızca uygulama gerektirdiğinde yüklenir. Örneğin, bir kullanıcı eklentisinde işlev kullanan bir kullanıcı arabirimi VSTO (örneğin, Şeritteki özel bir düğme).<br /><br /> Uygulama VSTO Eklentiyi başarıyla yüklerse **LoadBehavior** değeri 9 olarak kalır, ancak **COM** Eklentileri iletişim kutusundaki VSTO Eklentinin durumu, VSTO Eklentinin yüklü olduğunu belirtmek için güncelleştirilir. Eklentiyi yüklerken hata VSTO **LoadBehavior** değeri 8 olarak değişir.|
|16|Yüklü|İlk kez yükle, ardından isteğe bağlı yükle|Eklentinizin isteğe bağlı VSTO için bu değeri ayarlayın. Kullanıcı uygulamayı VSTO kez çalıştıracaksa uygulama eklentiyi yükler. Kullanıcı uygulamayı bir sonraki kez çalıştıracaksa, uygulama tarafından tanımlanan tüm kullanıcı arabirimi öğelerini VSTO yükler. Ancak kullanıcı VSTO kullanıcı arabirimi eklentiyle ilişkili bir kullanıcı arabirimi öğesini seçene kadar VSTO yüklenmez.<br /><br /> Uygulama VSTO eklentiyi ilk kez yükleyemedik mi, **LoadBehavior** değeri 16 kalırken VSTO yüklenir. Uygulama kapat edildikten sonra **LoadBehavior değeri** 9 olarak değişir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office mimarileri Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Çözüm Office oluşturma](../vsto/building-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
 