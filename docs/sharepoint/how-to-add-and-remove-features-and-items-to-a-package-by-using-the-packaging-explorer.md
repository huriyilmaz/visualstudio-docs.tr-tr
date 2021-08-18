---
title: 'Paketleme Gezgini: & öğeleri kaldırmak & ekleme'
titleSuffix: ''
description: Paket paketinde Paketleme Gezgini'ni kullanarak SharePoint ve öğeleri bir pakete Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0b40b21377c0ab566bb33adf3ac0d0f617f0c53c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106841"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Nasıl kullanılır: Paketleme Gezgini'ni kullanarak pakete özellik ve öğe ekleme ve kaldırma
  Paket öğelerini ve Özellikleri SharePoint için Paketleme Gezgini'ni kullanabilirsiniz. Proje öğelerinin ve SharePoint .wsp dosyanız içindeki özellikleri ayarlayabilirsiniz.

 Alternatif olarak, Etkinleştirme siparişlerini değiştirmek için Özellikler'i görüntülemek ve yeniden sıralamak için Paketleme Tasarımcısı'ni kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Add and remove features and items to a package by using the Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Paketleme Gezgini'ni açın
 Visual Studio çözümde en az bir proje varsa, Paketleme Gezgini'ni açmak için SharePoint kullanabilirsiniz. Alternatif olarak, Bir Özellik veya paket tasarımcısı görüntülenirken Paketleme Gezgini otomatik olarak açılır. Tüm Özellik ve paket tasarımcıları kapat sonra Paketleme Gezgini de kapanır.

#### <a name="to-open-the-packaging-explorer"></a>Paketleme Gezgini'ni açmak için

1. Menü çubuğunda Diğer Öğeleri **Görüntüle'yi**  >  **seçin Windows**  >  **Gezgini'ni seçin.**

     Paketleme **Gezgini** Araç Kutusunda **görünür.**

## <a name="adding-a-feature-to-a-package"></a>Pakete özellik ekleme
 Paketleme Gezgini'ni kullanarak bir Pakete yeni ve mevcut Özellikler ekleyebilirsiniz.

#### <a name="to-add-a-sharepoint-feature"></a>Bir SharePoint eklemek için

1. Paketleme **Gezgini'ni** açın, projenin kısayol menüsünü açın ve Özellik **Ekle'yi seçin.**

#### <a name="to-move-an-existing-sharepoint-feature"></a>Mevcut bir SharePoint taşımak için

1. Paketleme **Gezgini'ni** açın ve ardından aşağıdaki adımlardan birini gerçekleştirin:

    - Bir Özelliği **bir** projeden başka bir projeye sürükleyin.

    - Bir Özelliğin kısayol menüsünü açın, **Kes'i** seçin, Özelliği taşımak istediğiniz projenin kısayol menüsünü açın ve ardından Yapıştır'ı **seçin.**

    > [!NOTE]
    > Çözümünüzde birden fazla SharePoint varsa bu yordamı kullanın.

## <a name="validate-a-feature-or-package"></a>Bir özelliği veya paketi doğrulama
 Dosyaları doğrulaarak SharePoint özellikler ve paketler'de olası sorunları tanımlayabilirsiniz. Uyarılar ve hatalar Çıkış penceresinde ve Hata Listesi penceresinde görüntülenir.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Bir uygulama özelliğini SharePoint paketi doğrulamak için

1. Paketleme **Gezgini'ni açın.**

2. Özellik veya paket için bir kısayol menüsü açın ve doğrula'yı **seçin.**

## <a name="see-also"></a>Ayrıca bkz.
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
