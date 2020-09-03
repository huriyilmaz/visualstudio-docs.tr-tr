---
title: Etkileşim Desenleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f570d665ddbc97ccddf058e1bb424c62e23912cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825278"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio İçin Etkileşim Desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>Genel Bakış
 Tasarım alanı, genel olarak, benzer kısıtlamalar kümeleriyle ilgili sorunları gidermek için belirli durumlarda uygulanabilen bir tasarımın çekirdeğidir. Özellik ve sistem tasarımcıları bu tasarım düzenlerini başlangıç noktaları olarak kullanır ve bu sayede belirli durumlarına uyarlayabilirler.

 Visual Studio 'da yeni özellikler oluşturulurken göz önünde bulundurmanız gereken yaygın bir etkileşim desenleri kitaplığı vardır. Tasarım modellerimiz için iki temel bağlam vardır: Visual Studio Client (devenv) ve Visual Studio Online. Bazı tasarım sorunları için tüm durumlarda iyi bir şekilde çalışacak bir ubititous deseninin olması gerekir. Ancak çoğu durumda çözüm, bir tarayıcı içinde sunulan ve bir istemci uygulamasında barındırılan Kullanıcı arabirimi için farklı olabilir.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio Istemci model türleri

|Model türü|Description|Örnekler|
|------------------|-----------------|--------------|
|**Uygulama düzeyi desenleri**|Uygulamada ortak olan üst düzey desenler, uygulama bağlamını belirleme veya görüntüleme, ve bunlar içinde bileşik ve Denetim desenleri içeren|-Araç pencereleri<br />-Belge pencereleri|
|**Bileşik desenler**|Uygulama desenleri arasında yayılabilen ortak desenler veya ayrı bir yapılandırmadaki çeşitli denetimlerden oluşan tanınan bir desen|-Geçişi görüntüle<br />-Liste oluşturucular<br />-Verileri görüntüleme<br />-Bildirimler<br />-Doğrulama<br />-Seçim modelleri|
|**Denetim desenleri**|Düşük düzey denetimlerin davranış tahmini hakkında bilgiler|-Ağaç görünümleri<br />-Kılavuz denetimi içinde düzenleniyor|

## <a name="application-patterns"></a>Uygulama desenleri
 Yüksek düzeyde, Visual Studio arabirimi tek bir IDE içindeki birden çok pencere, iletişim kutusu, komut ve araç çubuğu içerir. Visual Studio hiyerarşisi bağlam ve sürücü menülerini belirler. IDE Kullanıcı arabirimindeki önemli tümleştirme noktaları belge pencereleri, araç pencereleri, projeler, komut yapısı, metin düzenleyici, araç kutusu, Özellikler penceresi ve araçlar > seçenekleridir.

 IDE 'nin Kullanıcı arabirimindeki her anahtar tümleştirme noktası için temel kullanım düzenleri vardır:

- [Visual Studio İçin Menüler ve Komutlar](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Pencere etkileşimleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Araç pencereleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Belge Düzenleyicisi kuralları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [İletişim Kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projeler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Ortak denetim desenleri
 Denetim desenleri, genellikle bireysel denetimlerin nasıl davranması beklendiğine ilişkin olarak yapılır. Bu, tutarlılığın en kritik olduğu bir alandır.

 Visual Studio 'daki yaygın denetimlerin çoğu, masaüstü Windows yönergelerini izlemelidir. Kılavuzlarımız yalnızca Visual Studio 'Ya özgü etkileşimlerle ortak kuralları geliştirmemiz gereken yerleri veya Visual Studio 'Yu gelişmiş kullanıcılarımızın ihtiyaçlarını karşılayacak şekilde uyarlamak için yönergelerin yerini tamamen yerine getirdiğimiz yerleri içerir.

- [Visual Studio İçin Yaygın Denetim Desenleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Ortak denetimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Bileşik desenler
 Kullanıcıların görevleri yerine getirmek için beklediği çeşitli yollar vardır. Mümkün olan yerlerde, Özellikler hem etkileşim hem de görsel tasarım için bu desenleri kullanacak şekilde tasarlanmalıdır.

 Visual Studio içinde çok sayıda bileşik desen olsa da, tutarlılığın en önemlileri şunlardır:

- [Visual Studio İçin Bileşik Desenler](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Nesne üzerinde kullanıcı arabirimi ve göz atma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Kalıcılık ve kaydetme ayarları](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
