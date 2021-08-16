---
title: Kodlanmış UI testleri için yapılandırma ve platformlar
description: Bu makalede, Visual Studio Enterprise için kodlanmış UI testleri için desteklenen yapılandırma ve platformlar bulunur.
ms.custom: SEO-VS-2020
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bf0e6afaff51c8305d349ba246261081583f36218533870310fbb54c8393bf62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395153"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar

Visual Studio Enterprise için kodlanmış uı testleri için desteklenen yapılandırma ve platformlar aşağıdaki tabloda listelenmiştir. Bu yapılandırma, kullanılarak oluşturulan eylem kayıtları için de geçerlidir [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)] .

> [!NOTE]
> Kodlanmış kullanıcı arabirimi test işlemi, test altındaki uygulama ile aynı ayrıcalıklara sahip olmalıdır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Desteklenen yapılandırmalar

| Yapılandırma | Desteklenir |
|-| - |
| İşletim Sistemleri | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| 32 bit / 64 bit Desteği | 32 bit çalıştıran 32 bit Windows, [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 32 bit uygulamaları test edebilir.<br /><br /> 32 bit çalıştıran 64 bit Windows, [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] uı eşitlemesi olan 32-bit WOW uygulamalarını test edebilir. n.<br /><br /> 32 bit çalıştıran 64 bit Windows, [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] kullanıcı arabirimi eşitlemesine sahip olmayan 64-bit Windows Forms ve WPF uygulamalarını test edebilir. |
| Mimari | x86 ve x64 **Not:**  Internet Explorer, veya sonraki sürümlerinde çalıştırılması dışında 64 bitlik modda desteklenmez [!INCLUDE[win8](../debugger/includes/win8_md.md)] . |
| .NET | .NET 2.0, 3.0, 3.5, 4 ve 4.5. **Note:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] ve Visual Studio her ikisi de .net 4 ' ün çalışması gerekir.   Ancak, listelenen .NET sürümleri kullanılarak geliştirilen uygulamalar desteklenir. |

> [!NOTE]
> *UI Eşitleme* , her bir denetimin ileti kuyruğunda kayıttan yürütmenin doğrulandığı bir özelliktir. Bir denetim kendisine gönderilen olaya yanıt vermiyorsa, olay yeniden gönderilir.

## <a name="platform-support"></a>Platform desteği

| Platform | Destek Düzeyi |
|-| - |
| Windows Phone Gör | yalnızca WinRT XAML tabanlı Telefon uygulamaları desteklenir. |
| UWP uygulamaları | Yalnızca XAML tabanlı UWP uygulamaları desteklenir. |
| Evrensel Windows Uygulamaları | yalnızca Telefon ve masaüstündeki XAML tabanlı evrensel Windows uygulamaları desteklenir. |
| Edge | Eylem adımlarının kaydı veya nesne özelliklerini görüntülemek için oluşturucunun kullanılması desteklenmiyor. testler, [kodlanmış uı çapraz tarayıcı testi uzantısı](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)kullanılarak Visual Studio 2015 güncelleştirme 2 ve sonraki sürümleri kullanılarak Edge tarayıcısında çalınabilir. |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **önemli:** Internet Explorer 10 yalnızca masaüstünde desteklenir.   <br /><br /> Internet Explorer 11 **Önemli:**  Internet Explorer 11 yalnızca masaüstünde desteklenir. | Tam olarak desteklendi.<br /><br /> -   **Internet Explorer 9 ve Internet Explorer 10 HTML5 desteği:** Kodlanmış UI testleri HTML5 denetimlerinin kaydını, çalınmasını ve doğrulanmasını destekler: ses, video, ProgressBar ve kaydırıcı. Daha fazla bilgi için bkz. [KODLANMıŞ UI TESTLERINDE HTML5 denetimleri kullanma](../test/using-html5-controls-in-coded-ui-tests.md). **Uyarı:**      Internet Explorer 10 içinde kodlanmış bir uı testleri oluşturursanız, ınternet explorer 9 veya ınternet explorer 8 kullanılarak çalışmayabilir. Bunun nedeni Internet Explorer 10'un Ses, Video, İlerleme Çubuğu ve Kaydırma gibi HTML5 denetimlerini içermesidir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.<br />-   **Internet Explorer 10 yazım denetimi desteği:** Internet Explorer 10 tüm metin kutuları için yazım denetimi yetenekleri içerir. Bu, önerilen düzeltmeler listesinden seçim yapmanızı sağlar. Kodlanmış UI Testi, alternatif yazım önerisi seçmek gibi kullanıcı eylemlerini yoksayar. Yalnızca metin kutusuna yazılan son metin kaydedilir.<br />     Yazım denetimini kullanan kodlanmış kullanıcı arabirimi testi için şu eylemler kaydedilir: Sözlüğe Ekle, Kopyala, Tümünü Seç, Sözlüğe Ekle ve Yoksay.<br />-   **Windows 8 altında çalışan 64 bit Internet Explorer desteği:** Daha önce, Internet Explorer 'ın 64 bitlik sürümleri, kayıt ve kayıttan yürütme için desteklenmez. [!INCLUDE[win8](../debugger/includes/win8_md.md)]Ve ile [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , Internet Explorer 'ın 64 bit sürümleri IÇIN kodlanmış UI testleri etkinleştirilmiştir. **Uyarı:**      64-Internet Explorer için bit desteği yalnızca [!INCLUDE[win8](../debugger/includes/win8_md.md)] veya sonraki sürümleri çalışırken geçerlidir.<br />-   **Internet Explorer 9 ' da sabitlenmiş siteler Için destek:** Internet Explorer 9 ' da sabitlenmiş siteler sunulmuştur. İliştirilmiş Sitelerle, sevdiğiniz sitelere önce Internet Explorer'ı açmak zorunda kalmadan doğrudan Windows görev çubuğundan ulaşabilirsiniz. Kodlanmış UI testleri iliştirilmiş sitelerde amaç duyarlı eylemler oluşturabilir. Sabitlenmiş siteler hakkında daha fazla bilgi için bkz. [sabitlenmiş siteler](https://support.microsoft.com/hub/4230784/internet-explorer-help).<br />-   **Internet Explorer 9 anlam etiketleri Için destek:** Internet Explorer 9, aşağıdaki anlamsal etiketleri sunmuştur: Section, NAV, article, as, hgroup, header, footer, şekil, figcaption ve Mark. Kodlanmış UI testleri kaydedilirken bu anlamsal etiketlerin tamamını yoksayar. Kodlanmış UI Test Oluşturucusu kullanarak bu etiketlere onaylama ekleyebilirsiniz. Bu öğelerin herhangi birine gidip özelliklerini görüntülemek için kodlandırılmış UI Test Oluşturucusu'nda gezinti aramayı kullanabilirsiniz.<br />-   **Internet Explorer sürümleri arasında beyaz boşluk karakterlerinin sorunsuz işlenmesi:** Internet Explorer 8, Internet Explorer 9 ve Internet Explorer 10 arasında boşluk karakterlerinin işlenmesinde farklılık vardır. Kodlanmış UI Testi bu farklılıkları sorunsuz bir şekilde işler. Dolayısıyla, örneğin, Internet Explorer 8'de oluşturulmuş bir kodlanmış UI testinin kayıttan oynatılması Internet Explorer 9 ve Internet Explorer 10'da başarıyla yapılabilir.<br />-   **Internet Explorer 'ın bildirim alanı artık "hatada devam et" özniteliği ayarlanmış olarak kaydedilir:** Internet Explorer 'ın bildirim alanındaki tüm eylemler artık "hatada devam et" özniteliği ayarlanmış olarak kaydedilir. Kayıttan yürütme sırasında bildirim çubuğu görünmüyorsa, eylemleri yoksayılır ve kodlanmış UI testi sonraki eylem ile devam eder. |
| Windows Forms ve WPF üçüncü taraf denetimleri | Tam olarak desteklendi.<br /><br /> Windows Formlar ve WPF uygulamalarında üçüncü taraf denetimleri etkinleştirmek için başvurular ve kod eklemeniz gerekir. Daha fazla bilgi için bkz. [denetimlerinizin KODLANMıŞ UI testlerini etkinleştirme](../test/enable-coded-ui-testing-of-your-controls.md). |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Desteklenmez. |
| Chrome<br /><br /> Firefox | Eylem adımlarını kaydetme desteklenmiyor. Kodlanmış UI Testleri Chrome ve Firefox tarayıcılarda Visual Studio 2012 Update 4 veya sonraki sürümüyle kayıttan yürütülebilir. Daha fazla ayrıntı için [buraya](using-different-web-browsers-with-coded-ui-tests.md) gidin. |
| Opera<br /><br /> Safari | Desteklenmez. |
| Silverlight | Desteklenmez.<br /><br /> ancak Visual studo 2013 için, Visual Studio galerisinden [Silverlight için Microsoft Visual Studio 2013 kodlu uı test eklentisini](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) indirebilirsiniz. |
| Flash/Java | Desteklenmez. |
| Windows Forms 2.0 ve ileri sürümü | Tam olarak desteklendi. **Note:**  NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez. |
| WPF 3.5 ve ileri sürümü | Tam olarak desteklendi.<br /><br /> **Göz önünde** NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez. |
| Windows Win32 | Bazı bilinen sorunlar ile çalışabilir, ancak resmi olarak desteklenmez. |
| MFC | Kısmen desteklenir. Desteklenen özelliklerin ayrıntıları için bkz. [UITest Framework](/archive/blogs/vstsqualitytools/uitest-framework-mfc-support-in-vs-2010) . |
| SharePoint | Tam olarak desteklendi. |
| Office İstemci Uygulamaları | Desteklenmez. |
| Dynamics CRM web istemcisi | Tam olarak desteklendi. |
| Dynamics (Ax) 2012 işlemcisi | Eylem kaydı ve kayıttan yürütme kısmen desteklenir. Ayrıntılar [Visual Studio Microsoft Dynamics için 10 kodlanmış kullanıcı arabirimi / eylem kaydı desteğine](/archive/blogs/dave_froslie/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012) bakın. |
| SAP | Desteklenmez. |
| Citrix/Terminal Hizmetleri | Terminal sunucusunda eylemleri kaydetmenizi önerilmez. Kaydedici aynı anda birden çok örnek çalıştırmayı desteklemez. |
| PowerBuilder | Kısmen desteklenir.<br /><br /> Desteğin kapsamı, PowerBuilder denetimleri için erişilebilirliğin etkin olduğu kadardır. |

Diğer platformları destekleyecek uzantılar oluşturma hakkında bilgi için bkz. Denetimlerinizin kodlanmış [UI](../test/enable-coded-ui-testing-of-your-controls.md) testini etkinleştirme ve Kodlanmış UI testlerini ve [eylem kayıtlarını genişletme.](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)