---
title: Kodlanmış UI testlerini yükseltme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1db5e653889f75931916c44de22e545415b53a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657258"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Visual Studio 2010'dan Kodlanmış UI Testlerini Yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 SP1 'de oluşturulan kodlanmış UI testlerini içeren test projeleri, Visual Studio 2012 açıldığında sessizce onarılır. Test projeleri kaynak denetimine işaretlenmişse, bu onarım için proje dosyaları kullanıma alınır. Onarıldıktan sonra, kodlanmış UI testlerini içeren bu test projeleri hem [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 hem de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] kullanılabilir.

 **Requirements**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio birden fazla test projesi türü içeriyor. Yeni bir kodlanmış UI testi oluşturursanız, bu, kodlanmış bir UI test projesi türünde oluşturulur. Daha fazla bilgi için bkz. [Visual Studio 'Nun önceki sürümlerinden testleri yükseltme](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> kodlanmış UI testleri içeren [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] test projelerini, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] veya [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ile yan yana [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] açtığınızda yeniden oluşturulmalıdır.

> [!WARNING]
> @No__t_0 içinde oluşturulan ve yalnızca birim testlerini içeren bir test projesi [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] açıldığında, kodlanmış UI testleri buna eklenemez. Benzer şekilde, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] içinde oluşturulan bir birim test projesine kodlanmış UI testi ekleyemezsiniz.

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Visual Studio 2010 ile Visual Studio 2012 arasındaki uyumluluk sorunları
 Aşağıdaki tabloda, [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ile [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] arasında kodlanmış UI testlerini geçirirken dikkat edilecek sorunlar listelenmektedir.

> [!CAUTION]
> Kodlanmış UI test projelerindeki başvurularla ilgili olarak Çözüm Gezgini görünmeyen bilinen bir sorun vardır. Daha fazla bilgi için [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] yükleme medyasına eklenen Benioku dosyasına bakın.

|Kodlanmış UI işlevselliği|Sorun|Çözüm|
|----------------------------|-----------|--------------|
|Silverlight UI test [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] desteklenmez|**Derleme başarısız olur**<br /><br /> @No__t_0 Feature Pack 2 ' ye sahipseniz ve Silverlight uygulamaları için kodlanmış UI testi projeleri oluşturduysanız, bu projeler [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] açılamaz.|Bu projeleri yalnızca [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 ' de yönetmenizi öneririz.|
|Firefox Kullanıcı Arabirimi testi [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] desteklenmez|**Derleme başarılı olur, test çalıştırması başarısız olur**<br /><br /> @No__t_0 Feature Pack 2 ' ye sahipseniz ve Firefox 'ta Web uygulamaları için kodlanmış UI testi projeleri oluşturduysanız, bu projeler [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] açılamaz.|Bu projeleri yalnızca [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 ' de yönetmenizi öneririz.|
|@No__t_0 yeni UI kod testi API 'Leri eklendi|**Derleme başarısız olur**<br /><br /> @No__t_0 ' de yeni UI testi API 'sini kullanarak kodlanmış UI testleri oluşturursanız, bu projeler [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] açılamaz.|Yeni API kullanan projeler yalnızca [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] yönetilmelidir.|
|@No__t_0, csproj dosyasında bir ' Select ' ifadesinin içine başvurular eklendi. @No__t_0, kodlanmış UI test derleme başvurularını dahil etmek için bir geri bildirim hedefi dosyası kullanıyoruz.|@No__t_0, kodlanmış UI testi içermeyen [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (veya SP1) içinde oluşturulmuş bir test projesine kodlanmış UI testi eklenemez.<br /><br /> Onarım işlemi, hedefler dosyasını ve SELECT ifadesini ekler. Kodlanmış UI testi Test projesinde değilse, Proje onarıldı olarak işaretlenir ve [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] kodlanmış UI testi eklenirken uygun başvurular eklenmez.|@No__t_0 kullanarak aynı çözümde yeni bir test projesi oluşturmanız ve buna yeni kodlanmış UI testinizi eklemeniz gerekecektir. Alternatif olarak, [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 'de test projesine kodlanmış UI testleri ekleyebilir ve bu projeyi [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] açabilirsiniz.|

## <a name="UpgradingCodedUIFromVS2010_Update"></a>Visual Studio 2010 SP1 güncelleştirmesi
 Visual Studio 2012 ve Windows 8 için uyumluluk desteğiyle [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 'e yönelik bir güncelleştirme, [Microsoft Indirme merkezi](http://www.microsoft.com/download/details.aspx?id=34677) 'nde ve ayrıca Visual Studio güncelleştirmesi olarak indirilebilir.

 Güncelleştirmeyi uyguladıktan sonra, Windows 8 için aşağıdaki [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 kodlanmış UI test aracı özellikleri geliştirilmiştir:

- Windows 8 çalıştıran bir bilgisayarda Microsoft .NET Framework 4,5 tabanlı Windows Presentation Foundation (WPF) denetimleri için kodlanmış UI testi çalıştırabilirsiniz.

- 64 bit (x64) Internet Explorer 10 için kodlanmış UI testini Windows 8 çalıştıran bir bilgisayarda çalıştırabilirsiniz.

  Güncelleştirme, aşağıdaki sorunlara yönelik düzeltmeler de içerir:

- **Kod kapsamı:** @No__t_1 SP1 'de Visual Studio 2012 tarafından oluşturulan bir kod kapsamı dosyası (. Coverage) açılamama.

- **Yabanlandırılan test yapıtları:** Takımınızın Team Foundation Server (TFS) 2010 ' de geçersiz bir kullanıcıya atanmış bir test yapıtı vardır. Örneğin, bir kullanıcı şirketten ayrıldı, ancak yine de kendisine atanan bir test durumuna sahip olur. TFS 2010 ' i TFS 2012 ' ye yükseltirsiniz. Yükseltilen TFS sunucusuna bağlanmak için [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 kullanın. @No__t_0 2010 ' i kullanarak test yapıtlarını herhangi bir TFS kullanıcılarına atayamazsınız.

- **Yük testi:** Yük testini bir bilgisayardaki yerel alan ağı (LAN) profili dışında bir ağ türü ile birlikte çalıştırdığınızda, ağ öykünücü sürücüsü işletim sisteminin kilitlenmesine neden olur. Daha ayrıntılı bilgi için bkz. [KB makalesi 2736182](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) Visual [Studio 'Nun önceki sürümlerinden testleri yükseltme](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) , [mevcut bir eylem kaydından](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [](../test/use-ui-automation-to-test-your-code.md) [kodlanmış UI testi oluşturma kodunuzu test etmek için UI Otomasyonunu kullanma Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
