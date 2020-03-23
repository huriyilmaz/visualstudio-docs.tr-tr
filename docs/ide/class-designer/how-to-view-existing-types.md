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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588713"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Nasıl yapılacağını: Sınıf Tasarımcısı'nda varolan türleri görüntüleme

Varolan bir türü ve üyelerini görmek için, şeklini sınıf diyagramına ekleyin.

Yerel ve başvurulan türleri görebilirsiniz. Yerel bir tür o anda açık olan projede mevcuttur ve okunur/yazılır. Başvurulan tür başka bir projede ya da başvurulan bir derlemede bulunur ve salt okunur özelliktedir.

Sınıf diyagramlarında yeni türler tasarlamak için [bkz.](how-to-create-types.md)

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Projedeki türleri bir sınıf diyagramı üzerinde görmek için

1. **Solution Explorer'daki**bir projeden varolan sınıf diyagramı (.cd) dosyayı açın. Ya da hiçbir sınıf diyagramı yoksa, projeye yeni bir sınıf diyagramı ekleyin. [Bkz. Nasıl: Projelere Sınıf Diyagramları Ekleyin.](how-to-add-class-diagrams-to-projects.md)

2. **Solution Explorer'daki**projeden, kaynak kodu dosyasını sınıf diyagramına sürükleyin.

    > [!NOTE]
    > Çözümünüzde birden çok uygulama arasında kod paylaşan bir proje varsa, dosyaları veya kodu yalnızca bu kaynaklardan sınıf diyagramına sürükleyebilirsiniz:
    >
    > - Diyagramı içeren uygulama projesi
    > - Uygulama projesi tarafından aktarılan paylaşılan bir proje
    > - Başvurulan bir proje
    > - Bir derleme

    Kaynak kodu dosyasında tanımlı türleri temsil eden şekiller, diyagram üzerinde dosyayı sürüklediğiniz konumda görünür.

**Ayrıca, Sınıf Görünümü'ndeki** proje düğümünden sınıf diyagramına bir veya daha fazla türü sürükleyerek projedeki türleri de görüntüleyebilirsiniz.

> [!TIP]
> **Sınıf Görünümü** açık değilse, **Görünüm** menüsünden **Sınıf Görünümü'nü** açın.

Diyagramdaki varsayılan konumlardaki türleri görüntülemek için Sınıf **Görünümü'nde**bir veya daha fazla tür seçin, seçili türleri sağ tıklatın ve **Sınıf Diyagramını Görüntüle'yi**seçin.

> [!NOTE]
> Türü içeren bir kapalı sınıf diyagramı projede zaten varsa, sınıf diyagramı açılarak tür şeklini görüntüler. Ancak, projede türü içeren sınıf diyagramı yoksa, **Sınıf Tasarımcısı** projede yeni bir sınıf diyagramı oluşturur ve türünü görüntülemek için açar.

Bir türü diyagram üzerinde ilk kez görüntülediğinizde, bu türe ait şekil varsayılan olarak daraltılmış görünür. Şekli genişleterek içeriğini görüntüleyebilirsiniz.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Bir projenin içeriğini sınıf diyagramında görüntülemek için

**Çözüm Gezgini** veya **Sınıf Görünümü'nde**projeyi sağ tıklatın ve **Görünüm'i**seçin, ardından **Sınıf Diyagramını Görüntüle'yi**seçin. Otomatik olarak doldurulan bir Sınıf Diyagramı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: Türler Arasında Devralma Yı Görüntüle](how-to-view-inheritance-between-types.md)
- [Nasıl? Sınıf Diyagramlarını Özelleştir](how-to-customize-class-diagrams.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
