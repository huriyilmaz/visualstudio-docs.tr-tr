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
ms.openlocfilehash: 6f814aabc4a6de4806fd419f16599758799c7538
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919128"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO eklentileri için kayıt defteri girişleri
  Visual Studio kullanılarak oluşturulan VSTO Eklentilerini dağıtırken belirli bir kayıt defteri girişi kümesi oluşturmanız gerekir. Bu kayıt defteri girdileri, Microsoft Office uygulamasının VSTO eklentisini bulmasını ve yüklemesini sağlayan bilgiler sağlar.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Projenizi yapılandırdığınızda, Visual Studio bu kayıt defteri girdilerini geliştirme bilgisayarında oluşturur, böylece VSTO eklentisini kolayca çalıştırıp hata ayıklaması yapabilirsiniz. VSTO eklentisini dağıtmak için ClickOnce kullanırsanız, kayıt defteri girdileri son kullanıcı bilgisayarında otomatik olarak oluşturulur. VSTO eklentisini dağıtmak için Windows Installer kullanıyorsanız, InstallShield Limited Edition projesini Son Kullanıcı bilgisayarında kayıt defteri girişlerini oluşturacak şekilde yapılandırmanız gerekir.

 VSTO eklentileri için yükleme işlemi sırasında kayıt girdilerinin nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Bu konuda, metin *EKLENTISI kimliği* , VSTO eklentisi için BENZERSIZ bir kimliği temsil eder. Varsayılan olarak, KIMLIK, VSTO eklenti derlemelerinizin adıdır.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Geçerli Kullanıcı ve tüm kullanıcılar için VSTO Eklentilerini Kaydet
 Bir VSTO eklentisi yüklendiğinde, bu iki şekilde kaydedilebilir:

- Yalnızca geçerli kullanıcı için (diğer bir deyişle, yalnızca VSTO eklentisi yüklendiğinde bilgisayarda oturum açan kullanıcı için kullanılabilir). Bu durumda, kayıt defteri girdileri **HKEY_CURRENT_USER**altında oluşturulur.

- Tüm kullanıcılar için (yani, bilgisayarda oturum açan tüm kullanıcılar VSTO eklentisini kullanabilir). Bu durumda, kayıt defteri girdileri **HKEY_LOCAL_MACHINE**altında oluşturulur.

  Visual Studio kullanarak oluşturduğunuz tüm VSTO eklentileri geçerli kullanıcı için kaydedilebilir. Ancak, VSTO eklentileri yalnızca belirli senaryolarda tüm kullanıcılar için kaydedilebilir. Bu senaryolar bilgisayardaki Microsoft Office sürümüne ve VSTO eklentisinin nasıl dağıtıldığına bağlıdır.

### <a name="deployment-type"></a>Dağıtım türü
 VSTO eklentisini dağıtmak için ClickOnce kullanırsanız, VSTO eklentisi yalnızca geçerli kullanıcı için kaydedilebilir. Bunun nedeni, ClickOnce 'ın yalnızca **HKEY_CURRENT_USER**altında anahtar oluşturulmasını destekler. Bir bilgisayarda bir VSTO eklentisini bir bilgisayardaki tüm kullanıcılara kaydetmek istiyorsanız, VSTO eklentisini dağıtmak için Windows Installer kullanmanız gerekir. Bu dağıtım türleri hakkında daha fazla bilgi için bkz. Windows Installer kullanarak [bir Office çözümünü ClickOnce kullanarak dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md) ve [Office çözümünü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Kayıt defteri girdileri
 Gerekli VSTO eklentisi kayıt defteri girdileri, *kökün* **HKEY_CURRENT_USER** veya yükleme geçerli kullanıcı veya tüm kullanıcılar için olduğuna bağlı olarak **HKEY_LOCAL_MACHINE** , aşağıdaki kayıt defteri anahtarlarının altında bulunur.

|Office uygulaması|Yapılandırma yolu|
|------------------|------------------|
|Visio|*Root*\Software\microsoft\\*Visio*\ AddIns\\*eklenti kimliği*|
|Diğer tüm|*Kök*\software\microsoft\office\\*Office uygulama adı*\ADDıNS\\*eklenti kimliği*|

> [!NOTE]
> Yükleyici, 64 bitlik Windows üzerindeki tüm kullanıcıları hedefliyorsanız, biri HKEY_LOCAL_MACHINE \Software\Microsoft ve HKEY_LOCAL_MACHINE \Software\\**Wow6432Node**\Microsoft Hive altında olmak üzere iki kayıt defteri girişi de içermesi önerilir. Bunun nedeni, kullanıcıların bilgisayarda Office 'in 32-bit veya 64 bit sürümlerini kullanması olasıdır.
>
>Yükleyici geçerli kullanıcıyı hedefliyorsanız, HKEY_CURRENT_USER \Software yolu paylaşıldığından, WOW6432Node 'e yüklemesi gerekmez.
>
>Daha fazla bilgi için lütfen bkz [. kayıt defterindeki 32-bit ve 64-bit uygulama verileri](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 Aşağıdaki tabloda bu kayıt defteri anahtarı altındaki girdiler listelenmektedir.

|Giriş|Tür|Değer|
|-----------|----------|-----------|
|**Açıklama**|REG_SZ|Gerekli. VSTO eklentisinin kısa bir açıklaması.<br /><br /> Bu açıklama, Kullanıcı Microsoft Office uygulamasındaki **Seçenekler** Iletişim kutusunun **Eklentiler** bölmesindeki VSTO eklentisini seçtiğinde görüntülenir.|
|**FriendlyName**|REG_SZ|Gerekli. Microsoft Office uygulamasındaki **com eklentileri** iletişim kutusunda görüntülenen VSTO eklentisinin açıklayıcı bir adı. Varsayılan değer VSTO eklenti KIMLIĞIDIR.|
|**LoadBehavior**|REG_DWORD|Gerekli. Uygulamanın VSTO eklentisini yükleme girişiminde bulunduğunu ve VSTO eklentisinin geçerli durumunu (yüklenen veya yüklenmeyen) belirten bir değer.<br /><br /> Varsayılan olarak, bu girdi 3 olarak ayarlanır ve bu, VSTO eklentisinin başlangıçta yüklendiğini belirtir. Daha fazla bilgi için bkz. [LoadBehavior değerleri](#LoadBehavior). **Note:**  Bir kullanıcı VSTO eklentisini devre dışı bırakırsa, bu eylem **HKEY_CURRENT_USER** kayıt defteri kovanında **LoadBehavior** değerini değiştirir. Her bir kullanıcı için, HKEY_CURRENT_USER Hive içindeki **LoadBehavior** değeri değeri **HKEY_LOCAL_MACHINE** Hive içinde tanımlanan varsayılan **LoadBehavior** 'yi geçersiz kılar.|
|**Bildirimi**|REG_SZ|Gerekli. VSTO eklentisinin dağıtım bildiriminin tam yolu. Yol, yerel bilgisayarda, bir ağ paylaşımında (UNC) veya bir Web sunucusu 'nda (HTTP) bir konum olabilir.<br /><br /> Çözümü dağıtmak için Windows Installer kullanırsanız, **bildirim** yoluna **File:///** önekini eklemeniz gerekir. Ayrıca, bu yolun sonuna  **&#124;vstolocal** (diğer bir deyişle, bu kanal karakteri **&#124;** , **vstolocal**tarafından izlenen) dizesini de eklemeniz gerekir. Bu, çözümünüzün ClickOnce önbelleği yerine yükleme klasöründen yüklenmesini sağlar. Daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Note:**  Geliştirme bilgisayarında bir VSTO eklentisi yapılandırdığınızda, Visual Studio bu kayıt defteri girişine  **&#124;vstolocal** dizesini otomatik olarak ekler.|

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
