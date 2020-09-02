---
title: Komut yerleştirme yönergeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d88a477403c98ff11c5f7303b55f5eb713b668c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195095"
---
# <a name="command-placement-guidelines"></a>Komut Yerleştirme Yönergeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamında (IDE) konumlandırma komutları için en iyi yöntemler, komut kümesinin boyutuna bağlı olarak değişiklik gösterir. Komutlar,. vsct dosyalarındaki bilgilere göre tanımlanır ve konumlandırılır.  
  
## <a name="best-practices-for-all-command-sets"></a>Tüm komut kümeleri için en iyi uygulamalar  
 Her komut kümesi için aşağıdaki yönergeleri izleyin:  
  
- Komut yapısının bir grafiğini önceden hazırlayın. Birden fazla konumda kullanılacak komutları, Birleşik giriş kutularını, komut gruplarını ve kısayol menülerini belirler.  
  
- Aynı grupta görünen komutların ilişkili olması gerekir.  
  
- Yalnızca bir komut içeren gruplar kabul edilebilir.  
  
- Paketler, var olan Visual Studio menülerine çok sayıda komut eklememelidir. Bunun yerine, yeni komutları barındırmak için menüler veya alt menüler oluşturmaları gerekir.  
  
- Varolan bir menüye komut yerleştirdiğinizde, amacı net olacak şekilde komutu adlandırın ve var olan komutlarla karıştırılmamalıdır.  
  
## <a name="best-practices-for-small-command-sets"></a>Küçük komut kümeleri için en iyi uygulamalar  
 Yalnızca birkaç komuta sahip bir VSPackage geliştiriyorsanız, bu yönergeleri de izleyin:  
  
- Mümkün olduğunda, uygun gruba koymak için bir komutun, Birleşik giriş kutusunun, grubun veya alt menünün [üst öğesini](../../extensibility/parent-element.md) kullanın.  
  
- Bu grupları VSPackage tarafından görüntülenecek menülere atayın.  
  
- Alt menünün veya bir komutun üst [öğesi bir Grup öğesi](../../extensibility/group-element.md)olmalıdır. Gruplara komutlar ve alt menüler atayın ve ardından grupları üst menülere atayın.  
  
- Komut tanımından sonra bir [CommandPlacements öğe](../../extensibility/commandplacements-element.md) bölümü ekleyerek ve sonra `CommandPlacements Element` her ek grup Için bir [commandyerleştirme öğesine](../../extensibility/commandplacement-element.md) ekleyerek ek gruplara bir komut koyabilirsiniz.  
  
## <a name="best-practices-for-large-command-sets"></a>Büyük komut kümeleri için en iyi uygulamalar  
 VSPackage 'ın birden çok bağlamda görünmesini sağlayacak çok sayıda komutu varsa, bu yönergeleri de izleyin:  
  
- Menüleri, grupları ve komutları kendi kendine üst öğe haline getirin. Diğer bir deyişle, `Parent Element` öğe tanımında bir öğesi atamayın.  
  
- `CommandPlacement Element` `CommandPlacements Element` Menüleri, grupları ve komutları ana menülere ve gruplarına yerleştirmek için bölümündeki girdileri kullanın.  
  
- `CommandPlacements`Bölümünde, belirli bir menüyü veya grubu dolduran girişler birbirine bitişik olmalıdır. Bu, okunabilirliği kolaylaştırır ve `Priority` dairelerin belirlenmesini kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
