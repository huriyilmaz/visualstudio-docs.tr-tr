---
title: Mağaza görüntüleyiciyi kullanarak hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654886"
---
# <a name="debugging-by-using-the-store-viewer"></a>Depo Görüntüleyiciyi Kullanarak Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mağaza Görüntüleyicisi ile [!INCLUDE[dsl](../includes/dsl-md.md)] tarafından kullanılan bir *deponun* durumunu inceleyebilirsiniz. Mağaza Görüntüleyici, belirli bir depoda bulunan tüm etki alanı model öğelerini, öğe özellikleri ve öğeler arasındaki bağlantılarla birlikte görüntüler.

## <a name="opening-store-viewer"></a>Mağaza Görüntüleyicisini açma
 Deneysel derleme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bir depo örneğinin model bilgilerini içerdiği bir kesme noktasında kodunuzu durdurun. Ardından **, komut penceresine aşağıdaki** komutu yazarak mağaza görüntüleyiciyi açın:

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> @No__t_0, mağaza örneğinizin adıyla değiştirmelisiniz. Ayrıca, ad alanını kodunuza eklerseniz, tam nitelikli ad alanı olmadan mağaza görüntüleyicisini görüntüleme komutunu yazabilirsiniz:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 @No__t_0 yönteminde birkaç aşırı yükleme vardır. Bir mağaza örneğini veya bir bölümü parametre olarak belirtebilirsiniz.

 Alternatif olarak, `Show` yöntemine geçirdiğiniz parametrenin kapsam içinde olduğu, kodunuzun içinde mağaza görüntüleyicisini görüntüleyen kod satırını yerleştirebilirsiniz. Bu eylem, kod satırı mağaza içeriğinin bir anlık görüntüsü olarak çalıştırıldığında mağaza görüntüleyiciyi görüntüler.

### <a name="using-store-viewer"></a>Mağaza görüntüleyicisini kullanma
 Mağaza Görüntüleyicisi açıldığında, aşağıdaki çizimde gösterildiği gibi kalıcı olmayan bir Windows Forms pencere görüntülenir.

 ![](../modeling/media/storeviewer2.png "storeviewer2")Mağaza Görüntüleyicisi

 Mağaza görüntüleyicisinde üç bölme bulunur: sol bölme, sağ üst bölme ve sağ alt bölme. Sol bölme, bir deponun `DomainDataDirectory` üyesinde bulunan türlerin ağaç görünümüdür. Bölüm düğümünü genişlettikten sonra bir öğeye tıklarsanız, öğenin özellikleri sağ üst bölmede görüntülenir. Öğe diğer öğelere bağlanmışsa, alt sağ bölmedeki ek öğeler görüntülenir. Sağ alt bölmedeki bir öğeye çift tıklarsanız, öğe sol bölmede vurgulanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
