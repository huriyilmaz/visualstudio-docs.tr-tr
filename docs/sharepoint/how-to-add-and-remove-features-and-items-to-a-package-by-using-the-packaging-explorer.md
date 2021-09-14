---
title: 'Paketleme Gezgini: pakete öğe & & Ekle veya Kaldır'
titleSuffix: ''
description: Visual Studio paketleme gezgini 'ni kullanarak bir SharePoint paketine özellikler ve öğeler ekleyin ve kaldırın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625130"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma
  SharePoint öğeleri ve özellikleri dağıtmak üzere bir paket yapılandırmak için paketleme gezgini ' ni kullanabilirsiniz. SharePoint proje öğelerini ve özelliklerini. wsp dosyanızın içinde ayarlayabilirsiniz.

 Alternatif olarak, etkinleştirme sırasını değiştirmek için özellikleri görüntülemek ve yeniden sıralamak üzere paketleme tasarımcısını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Paketleme Gezginini açın
 Visual Studio çözümünüz en az bir SharePoint projesi içeriyorsa paketleme gezgini 'ni açmak için aşağıdaki yordamı kullanabilirsiniz. Alternatif olarak, bir özellik veya paket tasarımcısını görüntülediğinizde paketleme Gezgini otomatik olarak açılır. Tüm özellik ve paket tasarımcılarını kapattıktan sonra paketleme Gezgini de kapanır.

#### <a name="to-open-the-packaging-explorer"></a>Paketleme Gezgini 'ni açmak için

1. menü çubuğunda   >  **diğer Windows**  >  **paketleme gezgini**' ni seçin.

     **Paketleme Gezgini** **araç kutusunda** görünür.

## <a name="adding-a-feature-to-a-package"></a>Bir pakete özellik ekleme
 Paketleme Gezgini 'ni kullanarak bir pakete yeni ve var olan özellikler ekleyebilirsiniz.

#### <a name="to-add-a-sharepoint-feature"></a>SharePoint özellik eklemek için

1. **Paketleme Gezginini** açın, proje için kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

#### <a name="to-move-an-existing-sharepoint-feature"></a>mevcut bir SharePoint özelliğini taşımak için

1. **Paketleme Gezginini** açın ve aşağıdaki adımlardan birini gerçekleştirin:

    - Bir **özelliği** bir projeden başka bir projeye sürükleyin.

    - Bir özelliğin kısayol menüsünü açın, **Kes**' i seçin, özelliği taşımak istediğiniz projenin kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    > [!NOTE]
    > çözümünüzde birden fazla SharePoint projeniz varsa, bu yordamı kullanın.

## <a name="validate-a-feature-or-package"></a>Bir özelliği veya paketi doğrulama
 dosyaları doğrulayarak SharePoint özellikleri ve paketlerdeki olası sorunları belirleyebilirsiniz. Uyarılar ve hatalar çıkış penceresinde ve Hata Listesi penceresinde görüntülenir.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>bir SharePoint özelliğini veya paketini doğrulamak için

1. **Paketleme Gezginini** açın.

2. Bir özellik veya paket için kısayol menüsünü açın ve ardından **Doğrula**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
