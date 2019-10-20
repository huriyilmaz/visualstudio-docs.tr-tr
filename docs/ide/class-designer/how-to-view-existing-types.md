---
title: 'Nasıl Yapılır: Varolan Türleri Görüntüleme (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 386b62e278b1fbe8230af16b54f8b7bb95857c48
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631528"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı varolan türleri görüntüleme

Var olan bir türü ve üyelerini görmek için, şeklini bir sınıf diyagramına ekleyin.

Yerel ve başvurulan türleri görebilirsiniz. Yerel bir tür o anda açık olan projede mevcuttur ve okunur/yazılır. Başvurulan tür başka bir projede ya da başvurulan bir derlemede bulunur ve salt okunur özelliktedir.

Sınıf diyagramlarında yeni türler tasarlamak için bkz. [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Projedeki türleri bir sınıf diyagramı üzerinde görmek için

1. **Çözüm Gezgini**bir projeden, varolan bir sınıf diyagramı (. CD) dosyasını açın. Ya da hiçbir sınıf diyagramı yoksa, projeye yeni bir sınıf diyagramı ekleyin. Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md).

2. **Çözüm Gezgini**projeden, bir kaynak kodu dosyasını sınıf diyagramına sürükleyin.

    > [!NOTE]
    > Çözümünüz birden çok uygulama arasında kod paylaşan bir proje içeriyorsa, dosyaları veya kodu yalnızca şu kaynaklardan bir sınıf diyagramına sürükleyebilirsiniz:
    >
    > - Diyagramı içeren uygulama projesi
    > - Uygulama Projesi tarafından içeri aktarılan paylaşılan bir proje
    > - Başvurulan bir proje
    > - Bir derleme

    Kaynak kodu dosyasında tanımlı türleri temsil eden şekiller, diyagram üzerinde dosyayı sürüklediğiniz konumda görünür.

Ayrıca, **sınıf görünümü** proje düğümünden bir veya daha fazla türü sınıf diyagramına sürükleyerek proje türlerini de görüntüleyebilirsiniz.

> [!TIP]
> **Sınıf görünümü** açık değilse, **Görünüm** menüsünden **sınıf görünümü** açın.

Diyagramdaki varsayılan konumlarda türleri görüntülemek için **sınıf görünümü**bir veya daha fazla tür seçin, seçili türlere sağ tıklayın ve **sınıf diyagramını görüntüle**' yi seçin.

> [!NOTE]
> Türü içeren bir kapalı sınıf diyagramı projede zaten varsa, sınıf diyagramı açılarak tür şeklini görüntüler. Ancak, projede türü içeren hiçbir sınıf diyagramı yoksa, **Sınıf Tasarımcısı** projede yeni bir sınıf diyagramı oluşturur ve türü göstermek için açar.

Bir türü diyagram üzerinde ilk kez görüntülediğinizde, bu türe ait şekil varsayılan olarak daraltılmış görünür. Şekli genişleterek içeriğini görüntüleyebilirsiniz.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Bir proje içeriğini bir sınıf diyagramında göstermek için

**Çözüm Gezgini** veya **sınıf görünümü**' de projeye sağ tıklayın ve **görüntüle**' yi seçin ve ardından **sınıf diyagramını görüntüle**' yi seçin. Otomatik olarak doldurulan bir Sınıf Diyagramı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Nasıl yapılır: sınıf diyagramlarını özelleştirme](how-to-customize-class-diagrams.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)