---
title: Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırma ve platformlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a4a049bca7ecb51a4b518c84b15d7dfa4ed3290f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301206"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Enterprise için kodlanmış UI testleri için desteklenen yapılandırma ve platformlar aşağıdaki tabloda listelenmiştir. Bu yapılandırma [!INCLUDE[MTRlong](../includes/mtrlong-md.md)]kullanılarak oluşturulan eylem kayıtları için de geçerlidir.

> [!NOTE]
> Kodlanmış kullanıcı arabirimi test işlemi, test altındaki uygulama ile aynı ayrıcalıklara sahip olmalıdır.

 **Requirements**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Desteklenen Yapılandırmalar

|Yapılandırma|Desteklenir|
|-------------------|---------------|
|İşletim Sistemleri|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|
|32 bit / 64 bit Desteği|32 bit [!INCLUDE[TCMext](../includes/tcmext-md.md)] çalıştıran 32 bit Windows, 32 bit uygulamaları test edebilir.<br /><br /> 32 bit [!INCLUDE[TCMext](../includes/tcmext-md.md)] çalıştıran 64 bit Windows, UI Eşitlemesi olan 32-bit WOW uygulamalarını test edebilir. n.<br /><br /> 32 bit [!INCLUDE[TCMext](../includes/tcmext-md.md)] çalıştıran 64 bit Windows, UI Eşitlemesi olmayan 64-bit Windows Forms ve WPF uygulamalarını test edebilir.|
|Mimari|x86 ve x64 **Not:** [!INCLUDE[win8](../includes/win8-md.md)] veya sonraki sürümlerde çalıştırmanın dışında 64 bitlik modda Internet Explorer desteklenmez.|
|.NET|.NET 2.0, 3.0, 3.5, 4 ve 4.5. **Note:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] ve Visual Studio 'nun her ikisi de .NET 4 ' ün çalışması gerekir. Ancak, listelenen .NET sürümleri kullanılarak geliştirilen uygulamalar desteklenir.|

> [!NOTE]
> *UI Eşitleme* , her bir denetimin ileti kuyruğunda kayıttan yürütmenin doğrulandığı bir özelliktir. Bir denetim kendisine gönderilen olaya yanıt vermiyorsa, olay yeniden gönderilir.

## <a name="platform-support"></a>Platform Desteği

|Platform|Destek Düzeyi|
|--------------|----------------------|
|Windows Phone Uygulamalar|Yalnızca WinRT XAML tabanlı telefon uygulamaları desteklenir.|
|Windows Mağazası Uygulamaları|Yalnızca XAML tabanlı Mağaza uygulamaları desteklenir.|
|Evrensel Windows Uygulamaları|Yalnızca telefon ve masaüstündeki XAML tabanlı Evrensel Windows uygulamaları desteklenir.|
|Kenar|Visual Studio 2015 güncelleştirme 2 ve sonraki sürümlerde [KODLANMıŞ UI çapraz tarayıcı testi uzantısını](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d) kullanarak|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Önemli:** Internet Explorer 10 yalnızca masaüstünde desteklenir. <br /><br /> Internet Explorer 11 **Önemli:** Internet Explorer 11 yalnızca masaüstünde desteklenir.|Tam olarak desteklendi.<br /><br /> **Internet Explorer 9 ve Internet Explorer 10 ' da HTML5 desteği -   :** kodlanmış UI testleri HTML5 denetimlerinin kaydını, çalınmasını ve doğrulanmasını destekler: ses, video, ProgressBar ve kaydırıcı. Daha fazla bilgi için bkz. [KODLANMıŞ UI TESTLERINDE HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md). **Uyarı:**      Internet Explorer 10 ' da kodlanmış UI testleri oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanılarak çalışmayabilir. Bunun nedeni Internet Explorer 10'un Ses, Video, İlerleme Çubuğu ve Kaydırma gibi HTML5 denetimlerini içermesidir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.<br />**Internet Explorer 10 yazım denetimi için -   desteği:** Internet Explorer 10, tüm metin kutuları için yazım denetimi yetenekleri içerir. Bu, önerilen düzeltmeler listesinden seçim yapmanızı sağlar. Kodlanmış UI Testi, alternatif yazım önerisi seçmek gibi kullanıcı eylemlerini yoksayar. Yalnızca metin kutusuna yazılan son metin kaydedilir.<br />     Yazım denetimini kullanan kodlanmış kullanıcı arabirimi testi için şu eylemler kaydedilir: Sözlüğe Ekle, Kopyala, Tümünü Seç, Sözlüğe Ekle ve Yoksay.<br />**Windows 8 ' de çalışan 64 bitlik Internet Explorer için -   desteği:** daha önce Internet explorer 'ın 64 bit sürümleri, kayıt ve kayıttan yürütme için desteklenmez. [!INCLUDE[win8](../includes/win8-md.md)] ve [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]ile, Internet Explorer 'ın 64 bitlik sürümleri için kodlanmış UI testleri etkinleştirilmiştir. **Uyarı:** 64-Internet Explorer için bit desteği yalnızca [!INCLUDE[win8](../includes/win8-md.md)] veya sonraki sürümleri çalıştırıyorsanız geçerlidir.<br />**Internet Explorer 9 ' da sabitlenmiş siteler için -   desteği:** Internet Explorer 9 ' da sabitlenmiş siteler sunulmuştur. İliştirilmiş Sitelerle, sevdiğiniz sitelere önce Internet Explorer'ı açmak zorunda kalmadan doğrudan Windows görev çubuğundan ulaşabilirsiniz. Kodlanmış UI testleri iliştirilmiş sitelerde amaç duyarlı eylemler oluşturabilir. Sabitlenmiş siteler hakkında daha fazla bilgi için bkz. [sabitlenmiş siteler](https://go.microsoft.com/fwlink/?LinkId=220037).<br />**Internet Explorer 9 anlam etiketleri için -   desteği:** Internet Explorer 9, aşağıdaki anlamsal etiketleri sunmuştur: Section, NAV, article, as, hgroup, header, footer, şekil, figcaption ve Mark. Kodlanmış UI testleri kaydedilirken bu anlamsal etiketlerin tamamını yoksayar. Kodlanmış UI Test Oluşturucusu kullanarak bu etiketlere onaylama ekleyebilirsiniz. Bu öğelerin herhangi birine gidip özelliklerini görüntülemek için kodlandırılmış UI Test Oluşturucusu'nda gezinti aramayı kullanabilirsiniz.<br />**Internet Explorer sürümleri arasında beyaz boşluk karakterlerinin sorunsuz işlenmesini -   :** Internet Explorer 8, Internet Explorer 9 ve Internet Explorer 10 arasında boşluk karakterlerinin işlenmesinde farklılık vardır. Kodlanmış UI Testi bu farklılıkları sorunsuz bir şekilde işler. Dolayısıyla, örneğin, Internet Explorer 8'de oluşturulmuş bir kodlanmış UI testinin kayıttan oynatılması Internet Explorer 9 ve Internet Explorer 10'da başarıyla yapılabilir.<br />**Internet Explorer 'ın bildirim alanı -   artık "hatada devam et" özniteliği ayarlanmış olarak kaydedilir:** Internet Explorer 'ın bildirim alanındaki tüm eylemler artık "hatada devam et" özniteliği ayarlanmış olarak kaydedilir. Kayıttan yürütme sırasında bildirim çubuğu görünmüyorsa, eylemleri yoksayılır ve kodlanmış UI testi sonraki eylem ile devam eder.|
|Windows Forms ve WPF üçüncü taraf denetimleri|Tam olarak desteklendi.<br /><br /> Windows Formlar ve WPF uygulamalarında üçüncü taraf denetimleri etkinleştirmek için başvurular ve kod eklemeniz gerekir. Daha fazla bilgi için bkz. [denetimlerinizin KODLANMıŞ UI testlerini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md).|
|Internet Explorer 6<br /><br /> Internet Explorer 7|Desteklenmez.|
|Chrome<br /><br /> Firefox|Eylem adımlarını kaydetme desteklenmiyor. Kodlanmış UI Testleri Chrome ve Firefox tarayıcılarda Visual Studio 2012 Update 4 veya sonraki sürümüyle kayıttan yürütülebilir. Daha fazla ayrıntı için [buraya](https://msdn.microsoft.com/library/jj835758.aspx) gidin.|
|Opera<br /><br /> Safari|Desteklenmez.|
|Silverlight|Desteklenmez.<br /><br /> Visual Studo 2013 için ancak Visual Studio galerisinden [Silverlight için Microsoft Visual Studio 2013 kodlu UI Test eklentisini](https://go.microsoft.com/fwlink/?LinkId=691026) indirebilirsiniz.|
|Flash/Java|Desteklenmez.|
|Windows Forms 2.0 ve ileri sürümü|Tam olarak desteklendi. **Note:**  NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez.|
|WPF 3.5 ve ileri sürümü|Tam olarak desteklendi.<br /><br /> **Göz önünde** NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez.|
|Windows Win32|Bazı bilinen sorunlar ile çalışabilir, ancak resmi olarak desteklenmez.|
|MFC|Kısmen desteklenir. Desteklenen özelliklerin ayrıntıları için aşağıdaki [Microsoft Web sitesine](https://go.microsoft.com/fwlink/?LinkId=206511) bakın.|
|SharePoint|Tam olarak desteklendi.|
|Office İstemci Uygulamaları|Desteklenmez.|
|Dynamics CRM web istemcisi|Tam olarak desteklendi.|
|Dynamics (Ax) 2012 işlemcisi|Eylem kaydı ve kayıttan yürütme kısmen desteklenir. Ayrıntılar için aşağıdaki [Microsoft Web sitesine](https://go.microsoft.com/fwlink/?LinkId=232677) bakın.|
|SAP|Desteklenmez.|
|Citrix/Terminal Hizmetleri|Bir Terminal sunucusunda eylemlerin kaydedilmesini önermeyiz. Kaydedici aynı anda birden çok örnek çalıştırmayı desteklemez.|
|PowerBuilder|Kısmen desteklenir.<br /><br /> Desteğin kapsamı, PowerBuilder denetimleri için erişilebilirliğin etkin olduğu kadardır.|

 Diğer platformları destekleyecek uzantılar oluşturma hakkında bilgi için bkz. [denetimlerinizin KODLANMıŞ UI testlerini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md) ve [Microsoft Excel 'ı desteklemek Için kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Mevcut bir eylem kaydından KODLANMıŞ UI testi oluşturma](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [kodunuzu test etmek Için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
