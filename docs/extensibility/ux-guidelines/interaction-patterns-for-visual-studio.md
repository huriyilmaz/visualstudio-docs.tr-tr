---
title: Visual Studio için Etkileşim Kalıpları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698371"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio İçin Etkileşim Desenleri
## <a name="overview"></a>Genel Bakış
 Tasarım deseni, genel olarak, benzer kısıtlama kümeleriyle ilgili sorunları çözmek için belirli durumlarda uygulanabilen bir tasarımın çekirdeğidir. Özellik ve sistem tasarımcıları bu tasarım modellerini başlangıç noktası olarak kullanırlar ve bu desenler daha sonra kendi özel durumlarına uyarlanabilir.

 Visual Studio, yeni özellikler oluştururken göz önünde bulundurulması gereken ortak etkileşim kalıpları kitaplığına sahiptir. Tasarım desenlerimiz için iki temel bağlam vardır: Visual Studio Client (devenv) ve Visual Studio Online. Bazı tasarım sorunları için, her durumda iyi çalışan bir her yerde desen vardır. Ancak, çoğu durumda, çözüm bir tarayıcı içinde sunulan ve istemci uygulamasında barındırılan Kullanıcı Arabirimi için farklı olabilir.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio İstemci desen türleri

|Desen türü|Açıklama|Örnekler|
|------------------|-----------------|--------------|
|**Uygulama düzeyi desenleri**|Uygulamada ortak olan, uygulama bağlamını belirleyen veya görüntüleyen ve bunların içinde bileşik ve kontrol desenleri içeren üst düzey desenler|- Takım pencereleri<br />- Belge pencereleri|
|**Kompozit desenler**|Uygulama desenleri arasında yayılabilecek ortak desenler veya farklı bir yapılandırmada çeşitli denetimlerden oluşan tanınan bir desen|- Görünüm anahtarlama<br />- Liste oluşturucuları<br />- Verilerin görüntülenmesi<br />- Bildirimler<br />- Doğrulama<br />- Seçim modelleri|
|**Kontrol desenleri**|Düşük seviyeli denetimlerin nasıl bir şekilde nasıl olması nın beklendiğine ilişkin ayrıntılar|- Ağaç görünümleri<br />- Izgara kontrolü içinde düzenleme|

## <a name="application-patterns"></a>Uygulama desenleri
 Yüksek düzeyde, Visual Studio arabirimi tek bir IDE içinde birden çok pencere, iletişim, komut ve araç çubuklarından oluşur. Visual Studio hiyerarşisi bağlamı belirler ve menüleri sürücüler. IDE'nin kullanıcı arabirimindeki önemli tümleştirme noktaları belge pencereleri, araç pencereleri, projeler, komut yapısı, metin düzenleyicisi, araç kutusu, Özellikler penceresi ve Araçlar > Seçenekleridir.

 IDE'nin kullanıcı arabirimindeki anahtar tümleştirme noktalarının her biri için temel kullanım desenleri vardır:

- [Visual Studio İçin Menüler ve Komutlar](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Pencere etkileşimleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Araç pencereleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Belge düzenleyicisi kuralları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [İletişim Kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projeler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Ortak kontrol desenleri
 Kontrol desenleri esas olarak tek tek denetimlerin nasıl bir şekilde nasıl olmasının beklendiğiyle ilgilidir. Bu tutarlılık en kritik olduğu bir alandır.

 Visual Studio'daki en yaygın denetimler Masaüstü Windows yönergelerine uymalıdır. Yönergelerimiz yalnızca Visual Studio'ya özel etkileşimlerle ortak sözleşmeleri genişletmemiz gereken alanları veya Visual Studio'yu sofistike kullanıcılarımızın ihtiyaçlarını karşılamak üzere uyarlamak için kuralların tamamen yerini aldığımız yerleri içerir.

- [Visual Studio İçin Yaygın Denetim Desenleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Ortak denetimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Kompozit desenler
 Kullanıcıların görevleri gerçekleştirmeyi beklemelerinin birkaç yolu vardır. Mümkün olan her yerde, özellikler bu desenleri hem etkileşim hem de görsel tasarım için kullanacak şekilde tasarlanmalıdır.

 Visual Studio içinde birçok kompozit desen olmakla birlikte, tutarlılık açısından en önemli bazıları şunlardır:

- [Visual Studio İçin Bileşik Desenler](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Nesne üzerinde ui ve gözetleme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Kalıcılık ve kaydetme ayarları](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
