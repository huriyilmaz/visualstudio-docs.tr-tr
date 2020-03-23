---
title: Kodlu UI Testleri için Yapılandırmalar ve Platformlar
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e18e50537f35080f9796f4a090b3806953ae5170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75845805"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar

Visual Studio Enterprise için kodlanmış UI testleri için desteklenen yapılandırmalar ve platformlar aşağıdaki tabloda listelenmiştir. Bu yapılandırmalar, '. [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]

> [!NOTE]
> Kodlanmış kullanıcı arabirimi test işlemi, test altındaki uygulama ile aynı ayrıcalıklara sahip olmalıdır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Desteklenen yapılandırmalar

| Yapılandırma | Destekleniyor |
|-| - |
| İşletim Sistemleri | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| 32 bit / 64 bit Desteği | 32 bit çalışan 32 bit [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Windows 32 bit uygulamaları sınayabilir.<br /><br /> 32 bit çalışan 64 bit [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Windows, UI Synchronization.n'ye sahip 32 bit WOW Uygulamalarını sınayabilir.<br /><br /> 32 bit [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] çalışan 64 bit Windows, Kullanıcı Birlemi Senkronizasyonu olmayan 64 bit Windows Formlarını ve WPF Uygulamalarını sınayabilir. |
| Mimari | x86 ve x64 **Not:** Internet Explorer, daha sonra sürümlerin [!INCLUDE[win8](../debugger/includes/win8_md.md)] altında veya daha sonraki sürümlerinde çalışmadığı sürece 64 bit modunda desteklenmez. |
| .NET | .NET 2.0, 3.0, 3.5, 4 ve 4.5. **Not:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Ve Visual Studio her ikisi de .NET 4 çalışması gerekir.   Ancak, listelenen .NET sürümleri kullanılarak geliştirilen uygulamalar desteklenir. |

> [!NOTE]
> *Kullanıcı Arabirimi Eşitlemesi,* her denetimin ileti kuyruğunda oynatmanın doğrulandığı bir özelliktir. Bir denetim kendisine gönderilen olaya yanıt vermiyorsa, olay yeniden gönderilir.

## <a name="platform-support"></a>Platform desteği

| Platform | Destek Düzeyi |
|-| - |
| Windows Phone Uygulamaları | Yalnızca WinRT-XAML tabanlı Telefon uygulamaları desteklenir. |
| UWP uygulamaları | Yalnızca XAML tabanlı UWP uygulamaları desteklenir. |
| Evrensel Windows Uygulamaları | Yalnızca Telefon ve Masaüstü'nde Yalnızca XAML tabanlı Evrensel Windows Uygulamaları desteklenir. |
| Edge | Eylem adımlarının kaydedilmesi veya nesne özelliklerini görüntülemek için oluşturucunun kullanılması desteklenmez. Testler, Visual Studio 2015 Update 2 ve sonraki sürümleri kullanılarak [Kodlanmış Kullanıcı Bira Sıtkı tarayıcı test uzantısı](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)kullanılarak Edge tarayıcıda oynatılabilir. |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Önemli:** Internet Explorer 10 yalnızca masaüstünde desteklenir. <br /><br /> Internet Explorer 11 **Önemli:** Internet Explorer 11 yalnızca masaüstünde desteklenir. | Tam olarak desteklendi.<br /><br /> -   **Internet Explorer 9 ve Internet Explorer 10'da HTML5 desteği:** Kodlanmış UI testleri HTML5 denetimlerinin kaydını, oynatımını ve doğrulanmasını destekler: Ses, Video, ProgressBar ve Kaydırıcı. Daha fazla bilgi için bkz: [Kodlanmış Kullanıcı Arabirimi testlerinde HTML5 denetimlerini kullanma.](../test/using-html5-controls-in-coded-ui-tests.md) **Uyarı:**      Internet Explorer 10'da kodlanmış bir ui testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanarak çalışmayabilir. Bunun nedeni Internet Explorer 10'un Ses, Video, İlerleme Çubuğu ve Kaydırma gibi HTML5 denetimlerini içermesidir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.<br />-   **Internet Explorer 10 Yazım Denetimi desteği:** Internet Explorer 10, tüm metin kutuları için yazım denetimi özelliklerini içerir. Bu, önerilen düzeltmeler listesinden seçim yapmanızı sağlar. Kodlanmış UI Testi, alternatif yazım önerisi seçmek gibi kullanıcı eylemlerini yoksayar. Yalnızca metin kutusuna yazılan son metin kaydedilir.<br />     Yazım denetimini kullanan kodlanmış kullanıcı arabirimi testi için şu eylemler kaydedilir: Sözlüğe Ekle, Kopyala, Tümünü Seç, Sözlüğe Ekle ve Yoksay.<br />-   **Windows 8 altında çalışan 64 bit Internet Explorer desteği:** Daha önce, Internet Explorer'ın 64 bit sürümleri kayıt ve oynatma için desteklenmedi. Ile [!INCLUDE[win8](../debugger/includes/win8_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]ve , kodlu UI testleri Internet Explorer 64 bit sürümleri için etkinleştirilmiştir. **Uyarı:** Internet Explorer için 64 bit destek yalnızca [!INCLUDE[win8](../debugger/includes/win8_md.md)] çalışırken veya daha sonra geçerlidir.<br />-   **Internet Explorer 9'da Sabitlenmiş Siteler desteği:** Internet Explorer 9'da sabitlenmiş siteler tanıtıldı. İliştirilmiş Sitelerle, sevdiğiniz sitelere önce Internet Explorer'ı açmak zorunda kalmadan doğrudan Windows görev çubuğundan ulaşabilirsiniz. Kodlanmış UI testleri iliştirilmiş sitelerde amaç duyarlı eylemler oluşturabilir. Sabitlenmiş siteler hakkında daha fazla bilgi için Bkz. [Sabitlenmiş siteler.](https://support.microsoft.com/hub/4230784/internet-explorer-help)<br />-   **Internet Explorer 9 Anlamsal Etiketler için Destek:** Internet Explorer 9 aşağıdaki semantik etiketleri tanıttı: bölüm, navigasyon, makale, kenara, hgroup, üstbilgi, altbilgi, şekil, incir başlık ve işareti. Kodlanmış UI testleri kaydedilirken bu anlamsal etiketlerin tamamını yoksayar. Kodlanmış UI Test Oluşturucusu kullanarak bu etiketlere onaylama ekleyebilirsiniz. Bu öğelerin herhangi birine gidip özelliklerini görüntülemek için kodlandırılmış UI Test Oluşturucusu'nda gezinti aramayı kullanabilirsiniz.<br />-   **Internet Explorer sürümleri arasında Beyaz Alan Karakterleri Sorunsuz Kullanımı:** Internet Explorer 8, Internet Explorer 9 ve Internet Explorer 10 arasındaki beyaz alan karakterlerinin işlenmesinde farklılıklar vardır. Kodlanmış UI Testi bu farklılıkları sorunsuz bir şekilde işler. Dolayısıyla, örneğin, Internet Explorer 8'de oluşturulmuş bir kodlanmış UI testinin kayıttan oynatılması Internet Explorer 9 ve Internet Explorer 10'da başarıyla yapılabilir.<br />-   **Internet Explorer Bildirim Alanı Şimdi "Hata devam" Öznitelik Kümesi ile kaydedilir:** Internet Explorer Bildirim Alanı'ndaki tüm eylemler artık "Hatada Devam Et" özniteliği kümesiyle kaydedilir. Kayıttan yürütme sırasında bildirim çubuğu görünmüyorsa, eylemleri yoksayılır ve kodlanmış UI testi sonraki eylem ile devam eder. |
| Windows Forms ve WPF üçüncü taraf denetimleri | Tam olarak desteklendi.<br /><br /> Windows Formlar ve WPF uygulamalarında üçüncü taraf denetimleri etkinleştirmek için başvurular ve kod eklemeniz gerekir. Daha fazla bilgi için [bkz.](../test/enable-coded-ui-testing-of-your-controls.md) |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Desteklenmiyor. |
| Chrome<br /><br /> Firefox | Eylem adımlarını kaydetme desteklenmiyor. Kodlanmış UI Testleri Chrome ve Firefox tarayıcılarda Visual Studio 2012 Update 4 veya sonraki sürümüyle kayıttan yürütülebilir. Daha fazla bilgi için [buraya](using-different-web-browsers-with-coded-ui-tests.md) gidin. |
| Opera<br /><br /> Safari | Desteklenmiyor. |
| Silverlight | Desteklenmiyor.<br /><br /> Ancak Visual Studo 2013 için [Silverlight için Microsoft Visual Studio 2013 kodlu UI test eklentisini](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) Visual Studio Gallery'den indirebilirsiniz. |
| Flash/Java | Desteklenmiyor. |
| Windows Forms 2.0 ve ileri sürümü | Tam olarak desteklendi. **Not:**  NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez. |
| WPF 3.5 ve ileri sürümü | Tam olarak desteklendi.<br /><br /> **Not** NetFx denetimleri tam olarak desteklenir, ancak tüm üçüncü taraf denetimleri desteklenmez. |
| Windows Win32 | Bazı bilinen sorunlar ile çalışabilir, ancak resmi olarak desteklenmez. |
| MFC | Kısmen desteklenir. Hangi özelliklerin [desteklendirilene](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) ilişkin ayrıntılar için Ara Bilgi çerçevesine bakın. |
| SharePoint | Tam olarak desteklendi. |
| Office İstemci Uygulamaları | Desteklenmiyor. |
| Dynamics CRM web istemcisi | Tam olarak desteklendi. |
| Dynamics (Ax) 2012 işlemcisi | Eylem kaydı ve kayıttan yürütme kısmen desteklenir. Ayrıntılar [için Microsoft Dynamics için Visual Studio 10 kodlu Kullanıcı Arabirimi / eylem kayıtları desteğine](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) bakın. |
| SAP | Desteklenmiyor. |
| Citrix/Terminal Hizmetleri | Eylemleri terminal sunucusunda kaydetmenizi önermiyoruz. Kaydedici aynı anda birden çok örneği çalıştırmayı desteklemez. |
| PowerBuilder | Kısmen desteklenir.<br /><br /> Desteğin kapsamı, PowerBuilder denetimleri için erişilebilirliğin etkin olduğu kadardır. |

Diğer platformları desteklemek için uzantılar oluşturma hakkında bilgi için, [denetimlerinizin kodlu Kullanıcı Arabirimi testini etkinleştir mesuliyye](../test/enable-coded-ui-testing-of-your-controls.md) ve [kodlanmış kullanıcı ara birimi testlerini ve eylem kayıtlarını genişletin'](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)e bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
