---
title: Visual Studio | için Etkileşim Desenleri Microsoft Docs
description: Daha fazla bilgi edinmek için yeni özellikler oluşturma konusunda kullanabileceğiniz ortak etkileşim Visual Studio.
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
ms.openlocfilehash: 7e47879db77ebe5888291e9c5b3b622ab66f85461d1993df670c5c2b22c567d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375136"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio İçin Etkileşim Desenleri
## <a name="overview"></a>Genel Bakış
 Genel olarak tasarım deseni, benzer kısıtlama kümeleriyle ilgili sorunları çözmek için belirli durumlarda uygulanan bir tasarımın temkisidir. Özellik ve sistem tasarımcıları bu tasarım desenlerini başlangıç noktaları olarak kullanır ve bu da daha sonra kendi durumlarına uyarlanabilir.

 Visual Studio, yeni özellikler oluşturmada dikkate alınacak ortak etkileşim desenlerinin bir kitaplığına sahiptir. Tasarım desenlerimiz için iki temel bağlam vardır: Visual Studio Client (devenv) ve GitHub Codespaces (eski adı Visual Studio Online). Bazı tasarım sorunlarında her durumda iyi çalışan bir desen vardır. Ancak çoğu durumda, bir tarayıcıda sunulan ve istemci uygulamasında barındırılan kullanıcı arabirimi için çözüm farklı olabilir.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio İstemci deseni türleri

|Desen türü|Açıklama|Örnekler|
|------------------|-----------------|--------------|
|**Uygulama düzeyinde desenler**|Uygulama için ortak üst düzey desenler, uygulama bağlamını belirleme veya görüntüleme ve bu bağlamların içinde bileşik ve denetim desenleri içeren|- Araç pencereleri<br />- Belge pencereleri|
|**Bileşik desenler**|Uygulama desenlerini kapsayan yaygın desenler veya ayrı bir yapılandırmada çeşitli denetimlerden yapılmış tanınan bir desen|- Değiştirmeyi görüntüleme<br />- Oluşturucuları listele<br />- Verileri görüntüleme<br />- Bildirimler<br />- Doğrulama<br />- Seçim modelleri|
|**Denetim desenleri**|Alt düzey denetimlerin nasıl davranması gerektiğine yönelik özeller|- Ağaç görünümleri<br />- Kılavuz denetimi içinde düzenleme|

## <a name="application-patterns"></a>Uygulama desenleri
 Üst düzeyde, Visual Studio arabirimi tek bir IDE içinde birden çok pencere, iletişim kutusu, komut ve araç çubuğundan oluşur. Bu Visual Studio, bağlam ve sürücü menülerini belirler. IDE'nin kullanıcı arabiriminde önemli tümleştirme noktaları belge pencereleri, araç pencereleri, projeler, komut yapısı, metin düzenleyicisi, araç kutusu, Özellikler penceresi ve Araçlar > Seçenekleridir.

 IDE'nin kullanıcı arabiriminde anahtar tümleştirme noktalarının her biri için temel kullanım desenleri vardır:

- [Visual Studio İçin Menüler ve Komutlar](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Pencere etkileşimleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Araç pencereleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Belge düzenleyicisi kuralları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [İletişim Kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projeler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Ortak denetim desenleri
 Denetim düzenleri temelde tek tek denetimlerin nasıl davranması beklendiğiyle ilgilidir. Bu, tutarlılığı en kritik olan alandır.

 En yaygın denetimler Visual Studio Desktop uygulaması yönergelerine Windows gerekir. Yönergelerimiz yalnızca ortak kuralları Visual Studio'a özgü etkileşimlerle artırmamız gereken alanları veya gelişmiş kullanıcılarımızın ihtiyaçlarını karşılamak üzere Visual Studio uyarlamak için yönergeleri tamamen yenilelarımızın yer alan alanlarını içerir.

- [Visual Studio İçin Yaygın Denetim Desenleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Ortak denetimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Bileşik desenler
 Kullanıcıların görevleri gerçekleştirmeyi beklemesi için çeşitli yollar vardır. Mümkün olan her yerde özellikler hem etkileşim hem de görsel tasarım için bu desenleri kullanmak üzere tasarlanmalı.

 Verilerde birçok bileşik desen Visual Studio, ancak tutarlılık açısından en önemlilerinden bazıları:

- [Visual Studio İçin Bileşik Desenler](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Nesne kullanıcı arabirimi ve göz atma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Kalıcılık ve ayarları kaydetme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
