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
ms.openlocfilehash: 3a29e531ca9b2a74e67abf80a0e3017a0f5b0b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297996"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Visual Studio 2010'dan Kodlanmış UI Testlerini Yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SP1 'de oluşturulan kodlanmış UI testlerini içeren test projeleri [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , Visual Studio 2012 açıldığında sessizce onarılır. Test projeleri kaynak denetimine işaretlenmişse, bu onarım için proje dosyaları kullanıma alınır. Onarıldıktan sonra, kodlanmış UI testlerini içeren bu test projeleri hem SP1 hem de için kullanılabilir [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

 **Gereksinimler**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio birden fazla test projesi türü içeriyor. Yeni bir kodlanmış UI testi oluşturursanız, bu, kodlanmış bir UI test projesi türünde oluşturulur. Daha fazla bilgi için bkz. [Visual Studio 'Nun önceki sürümlerinden testleri yükseltme](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] kodlanmış UI testleri içeren test projelerinin, içinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] veya yan yana içinde açtığınızda yeniden oluşturulması gerekir [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

> [!WARNING]
> İçinde oluşturulan [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ve yalnızca birim testlerini içeren bir test projesi içinde açıldığında [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , kodlanmış UI testleri buna eklenemez. Benzer şekilde, içinde oluşturulan bir birim test projesine kodlanmış UI testi ekleyemezsiniz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Visual Studio 2010 ile Visual Studio 2012 arasındaki uyumluluk sorunları
 Aşağıdaki tabloda, ve arasında kodlanmış UI testlerini geçirirken dikkat edilecek sorunlar listelenmektedir [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

> [!CAUTION]
> Kodlanmış UI test projelerindeki başvurularla ilgili olarak Çözüm Gezgini görünmeyen bilinen bir sorun vardır. Daha fazla bilgi için yükleme medyasına eklenen Benioku dosyasına bakın [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

|Kodlanmış UI işlevselliği|Sorun|Çözüm|
|----------------------------|-----------|--------------|
|' De Silverlight UI testi desteklenmez [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Derleme başarısız olur**<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]Feature Pack 2 ' ye sahipseniz ve Silverlight uygulamaları Için KODLANMıŞ UI testi projeleri oluşturduysanız, bu projeler içinde açılamaz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|Bu projeleri [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yalnızca Feature Pack 2 ' de yönetmenizi öneririz.|
|Firefox Kullanıcı Arabirimi testi, içinde desteklenmez [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Derleme başarılı olur, test çalıştırması başarısız olur**<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]Özellik paketi 2 ' ye sahipseniz ve Firefox 'ta Web uygulamaları Için KODLANMıŞ UI testi projesi oluşturduysanız, bu projeler içinde açılamaz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|Bu projeleri [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yalnızca Feature Pack 2 ' de yönetmenizi öneririz.|
|Yeni Kullanıcı arabirimi kod testi API 'Leri eklendi [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Derleme başarısız olur**<br /><br /> İçinde yeni UI testi API 'sini kullanarak kodlanmış UI testleri oluşturursanız [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , bu projeler içinde açılamaz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] .|Yeni API kullanan projeler yalnızca ' de yönetilmelidir [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|
|' De [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ,, csproj dosyasındaki bir ' Select ' ifadesinin içine başvurular eklendi. İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , KODLANMıŞ UI test derleme başvurularını dahil etmek için bir geri bildirim hedefi dosyası kullanıyoruz.|' De [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , KODLANMıŞ [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] UI testi içermeyen (veya SP1) içinde oluşturulmuş bir test PROJESINE kodlanmış UI testi eklenemez.<br /><br /> Onarım işlemi, hedefler dosyasını ve SELECT ifadesini ekler. Kodlanmış UI testi Test projesinde değilse, Proje onarıldı olarak işaretlenir ve kodlanmış UI testi eklenirken ilgili başvurular eklenmez [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|Kullanarak aynı çözümde yeni bir test projesi oluşturmanız [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ve buna yeni KODLANMıŞ UI testinizi eklemeniz gerekecektir. Alternatif olarak, SP1 'deki test projesine kodlanmış UI testleri ekleyebilir [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ve içinde bu projeyi açabilirsiniz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|

## <a name="visual-studio-2010-sp1-update"></a><a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 güncelleştirmesi
 [!INCLUDE[vs2010](../includes/vs2010-md.md)]Visual studio 2012 ve Windows 8 için uyumluluk desteğiyle SP1 'e yönelik bir güncelleştirme, [Microsoft İndirme Merkezi](https://www.microsoft.com/download/details.aspx?id=34677) ' nde ve ayrıca Visual Studio güncelleştirmesi olarak indirilebilir.

 Güncelleştirmeyi uyguladıktan sonra, aşağıdaki [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 kodlu UI test aracı özellikleri Windows 8 için geliştirilmiştir:

- Windows 8 çalıştıran bir bilgisayarda Microsoft .NET Framework 4,5 tabanlı Windows Presentation Foundation (WPF) denetimleri için kodlanmış UI testi çalıştırabilirsiniz.

- 64 bit (x64) Internet Explorer 10 için kodlanmış UI testini Windows 8 çalıştıran bir bilgisayarda çalıştırabilirsiniz.

  Güncelleştirme, aşağıdaki sorunlara yönelik düzeltmeler de içerir:

- **Kod kapsamı:** SP1 'de Visual Studio 2012 tarafından oluşturulan bir kod kapsamı dosyası (. Coverage) açılamama [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

- **Yabanlandırılan test yapıtları:** Takımınızın Team Foundation Server (TFS) 2010 ' de geçersiz bir kullanıcıya atanmış bir test yapıtı vardır. Örneğin, bir kullanıcı şirketten ayrıldı, ancak yine de kendisine atanan bir test durumuna sahip olur. TFS 2010 ' i TFS 2012 ' ye yükseltirsiniz. [!INCLUDE[TCMext](../includes/tcmext-md.md)]YÜKSELTILEN TFS sunucusuna bağlanmak için 2010 kullanırsınız. Test yapıtlarını 2010 kullanarak herhangi bir TFS kullanıcılarına atayamazsınız [!INCLUDE[TCMext](../includes/tcmext-md.md)] .

- **Yük testi:** Yük testini bir bilgisayardaki yerel alan ağı (LAN) profili dışında bir ağ türü ile birlikte çalıştırdığınızda, ağ öykünücü sürücüsü işletim sisteminin kilitlenmesine neden olur. Daha ayrıntılı bilgi için bkz. [KB makalesi 2736182](https://support.microsoft.com/help/2736182/a-gdr-update-for-visual-studio-2010-sp1-is-available-to-add-compatibil).

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) Visual [Studio 'Nun önceki sürümlerinden testleri yükseltme](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) , [mevcut bir eylemden kodlanmış bir UI testi oluşturma](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) , [kodlanmış UI testleri ve eylem kayıtları Için desteklenen yapılandırma ve platformları](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
