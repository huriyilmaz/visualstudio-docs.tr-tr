---
title: Komut yerleştirme yönergeleri | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (ıde) konumlandırma komutları için kılavuzları ve en iyi uygulamaları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f0e78221b93d766b8dd0f018501f3fc808a98c16
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029014"
---
# <a name="command-placement-guidelines"></a>Komut yerleştirme yönergeleri
Visual Studio tümleşik geliştirme ortamındaki (ıde) konumlandırma komutlarının en iyi yöntemleri, komut kümesinin boyutuna bağlı olarak değişir. Komutlar, *. vsct* dosyalarındaki bilgilere göre tanımlanır ve konumlandırılır.

## <a name="best-practices-for-all-command-sets"></a>Tüm komut kümeleri için en iyi uygulamalar
 Her komut kümesi için aşağıdaki yönergeleri izleyin:

- Komut yapısının bir grafiğini önceden hazırlayın. Birden fazla konumda kullanılacak komutları, Birleşik giriş kutularını, komut gruplarını ve kısayol menülerini belirler.

- Aynı grupta görünen komutların ilişkili olması gerekir.

- Yalnızca bir komut içeren gruplar kabul edilebilir.

- paketler varolan Visual Studio menülere çok sayıda komut eklememelidir. Bunun yerine, yeni komutları barındırmak için menüler veya alt menüler oluşturmaları gerekir.

- Varolan bir menüye komut yerleştirdiğinizde, amacı net olacak şekilde komutu adlandırın ve var olan komutlarla karıştırılmamalıdır.

## <a name="best-practices-for-small-command-sets"></a>Küçük komut kümeleri için en iyi uygulamalar
 Yalnızca birkaç komuta sahip bir VSPackage geliştiriyorsanız, bu yönergeleri de izleyin:

- Mümkün olduğunda, uygun gruba koymak için bir komutun, Birleşik giriş kutusunun, grubun veya alt menünün [üst](../../extensibility/parent-element.md) öğesini kullanın.

- Bu grupları VSPackage tarafından görüntülenecek menülere atayın.

- Alt menünün veya bir komutun üst öğesi bir [Grup](../../extensibility/group-element.md) öğesi olmalıdır. Gruplara komutlar ve alt menüler atayın ve ardından grupları üst menülere atayın.

- Komutun tanımından sonra bir [CommandPlacements](../../extensibility/commandplacements-element.md) öğe bölümü ekleyerek ve sonra `CommandPlacements` her ek grup Için bir [commandyerleştirme](../../extensibility/commandplacement-element.md) öğesine ekleyerek ek gruplara bir komut koyabilirsiniz.

## <a name="best-practices-for-large-command-sets"></a>Büyük komut kümeleri için en iyi uygulamalar
 VSPackage 'ın birden çok bağlamda görünmesini sağlayacak çok sayıda komutu varsa, bu yönergeleri de izleyin:

- Menüleri, grupları ve komutları kendi kendine üst öğe haline getirin. Diğer bir deyişle, `Parent` öğe tanımında bir öğe atamayın.

- `CommandPlacement` `CommandPlacements` Menü, Grup ve komutları ana menülere ve gruplarına yerleştirmek için öğe bölümündeki öğe girdilerini kullanın.

- `CommandPlacements`Öğe bölümünde, belirli bir menüyü veya grubu dolduran girişler birbirine bitişik olmalıdır. Bu, okunabilirliği kolaylaştırır ve `Priority` dairelerin belirlenmesini kolaylaştırır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [komut tablosu (. vsct) dosyaları Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
