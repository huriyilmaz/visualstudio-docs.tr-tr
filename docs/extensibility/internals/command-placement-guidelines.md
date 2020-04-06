---
title: Komut Yerleştirme Yönergeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709562"
---
# <a name="command-placement-guidelines"></a>Komut yerleştirme yönergeleri
Visual Studio tümleşik geliştirme ortamında (IDE) konumlandırma komutları için en iyi uygulamalar komut kümesinin boyutuna bağlı olarak değişir. Komutlar *.vsct* dosyalarındaki bilgilere göre tanımlanır ve konumlandırılır.

## <a name="best-practices-for-all-command-sets"></a>Tüm komut kümeleri için en iyi uygulamalar
 Her komut kümesi için aşağıdaki yönergeleri izleyin:

- Komut yapısının bir grafiğini önceden hazırlayın. Birden fazla konumda kullanılacak komutları, açılan kutuları, komut gruplarını ve kısayol menülerini tanımlayın.

- Aynı grupta görünen komutlar ilişkili olmalıdır.

- Yalnızca bir komut içeren gruplar kabul edilebilir.

- Paketler, varolan Visual Studio menülerine çok sayıda komut eklememelidir. Bunun yerine, yeni komutları barındırmak için menüler veya alt menüler oluşturmaları gerekir.

- Varolan bir menüye bir komut koyduğunuzda, amacının açık olması ve varolan komutlarla karıştırılmayan komutu adlandırın.

## <a name="best-practices-for-small-command-sets"></a>Küçük komut kümeleri için en iyi uygulamalar
 Sadece birkaç komutu olan bir VSPackage geliştiriyorsanız, aşağıdaki yönergeleri de uygulayın:

- Mümkün olduğunda, uygun gruba koymak için bir komut, açılan kutu, grup veya alt menü [Üst](../../extensibility/parent-element.md) öğesini kullanın.

- Bu grupları VSPackage tarafından görüntülenen menülere atayın.

- Alt menünün veya komutun üst öğesi bir [Grup](../../extensibility/group-element.md) öğesi olmalıdır. Gruplara komutlar ve alt menüler atayın ve ardından grupları üst menülere atayın.

- Komutun tanımından sonra bir [Komut Yerleşimleri](../../extensibility/commandplacements-element.md) öğesi bölümü ekleyerek ve daha sonra her `CommandPlacements` ek grup için bir [Komut Yerleştirme](../../extensibility/commandplacement-element.md) öğesi öğesi öğesini öğeyi ekleyerek ek gruplara bir komut koyabilirsiniz.

## <a name="best-practices-for-large-command-sets"></a>Büyük komut kümeleri için en iyi uygulamalar
 VSPackage'ınızda birden çok bağlamda görünecek birçok komut varsa, aşağıdaki yönergeleri de izleyin:

- Menüler, gruplar ve komutlar kendi kendine ebeveynlik olun. Diğer bir deyişle, öğenin tanımında bir `Parent` öğe atamayın.

- Menüleri, grupları `CommandPlacements` ve komutları üst menülerine ve gruplarına koymak için öğe bölümündeki öğe girişlerini kullanın. `CommandPlacement`

- `CommandPlacements` Öğe bölümünde, belirli bir menü veya grubu dolduran girişler birbirine bitişik olmalıdır. Bu, okunabilirliğe yardımcı `Priority` olur ve sıralamaları belirlemeyi kolaylaştırır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
