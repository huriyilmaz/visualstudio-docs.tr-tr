---
title: BoundsRules şekil konumunu ve boyutunu kısıtlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672724"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules Şekil Konumunu ve Boyutunu Kısıtlamama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Sınır kuralı* , bir şeklin boyut ve konum sınırlarını tanımlayan bir sınıftır. Bir Kullanıcı bir şekli veya bir şeklin köşelerini ya da yüzlerini sürüklerken sürekli olarak çağrılan bir yöntem sağlar.

 Aşağıdaki örnek, dikdörtgen bir şekli sabit boyutun yatay veya dikey bir çubuğu olacak şekilde kısıtlar. Kullanıcı köşeleri veya kenarları sürüklediğinde, ana hat yükseklik ve genişlik için izin verilen iki yapılandırma arasında ters döndürülür.

 Sınır kuralı <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> türetilmiş bir sınıftır. Şekil içinde kuralın bir örneği oluşturulur:

```
using Microsoft.VisualStudio.Modeling.Diagrams; ...
public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}
/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

 İsterseniz hem konum hem de boyutun kısıtlandığına dikkat edin.

## <a name="see-also"></a>Ayrıca Bkz.
 [değişikliklere yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md) <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
