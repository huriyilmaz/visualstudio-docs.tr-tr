---
title: Visual Studio için etkileşim desenleri | Microsoft Docs
description: Visual Studio için yeni özellikler oluştururken kullanabileceğiniz ortak etkileşim desenlerinin Kitaplığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1d93d4b99b99a2a833d3301f32a5005d6dda3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152048"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio İçin Etkileşim Desenleri
## <a name="overview"></a>Genel Bakış
 Tasarım alanı, genel olarak, benzer kısıtlamalar kümeleriyle ilgili sorunları gidermek için belirli durumlarda uygulanabilen bir tasarımın çekirdeğidir. Özellik ve sistem tasarımcıları bu tasarım düzenlerini başlangıç noktaları olarak kullanır ve bu sayede belirli durumlarına uyarlayabilirler.

 Visual Studio, yeni özellikler oluşturulurken göz önünde bulundurmanız gereken yaygın bir etkileşim desenleri kitaplığı içerir. tasarım modellerimiz için iki temel bağlam vardır: Visual Studio Client (devenv) ve GitHub codespaces (eski Visual Studio adıyla çevrimiçi). Bazı tasarım sorunları için tüm durumlarda iyi bir şekilde çalışacak bir ubititous deseninin olması gerekir. Ancak çoğu durumda çözüm, bir tarayıcı içinde sunulan ve bir istemci uygulamasında barındırılan Kullanıcı arabirimi için farklı olabilir.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio İstemci model türleri

|Model türü|Açıklama|Örnekler|
|------------------|-----------------|--------------|
|**Uygulama düzeyi desenleri**|Uygulamada ortak olan üst düzey desenler, uygulama bağlamını belirleme veya görüntüleme, ve bunlar içinde bileşik ve Denetim desenleri içeren|-Araç pencereleri<br />-Belge pencereleri|
|**Bileşik desenler**|Uygulama desenleri arasında yayılabilen ortak desenler veya ayrı bir yapılandırmadaki çeşitli denetimlerden oluşan tanınan bir desen|-Geçişi görüntüle<br />-Liste oluşturucular<br />-Verileri görüntüleme<br />-Bildirimler<br />-Doğrulama<br />-Seçim modelleri|
|**Denetim desenleri**|Düşük düzey denetimlerin davranış tahmini hakkında bilgiler|-Ağaç görünümleri<br />-Kılavuz denetimi içinde düzenleniyor|

## <a name="application-patterns"></a>Uygulama desenleri
 yüksek düzeyde Visual Studio arabirimi, tek bir ıde içindeki birden çok pencere, iletişim kutusu, komut ve araç çubuğu içerir. Visual Studio hiyerarşisi bağlam ve sürücü menülerini belirler. IDE Kullanıcı arabirimindeki önemli tümleştirme noktaları belge pencereleri, araç pencereleri, projeler, komut yapısı, metin düzenleyici, araç kutusu, Özellikler penceresi ve araçlar > seçenekleridir.

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

 Visual Studio en yaygın denetimleri masaüstü Windows yönergelerine uymalıdır. kılavuzlarımız yalnızca Visual Studio özgü etkileşimler ile ortak kuralları geliştirmemiz gereken ve yalnızca Visual Studio gelişmiş kullanıcılarımızın ihtiyaçlarını karşılayacak şekilde kuralları tamamen yerine getirdiğimiz yerlerden oluşan bölgeleri içerir.

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
