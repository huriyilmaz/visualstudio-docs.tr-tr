---
title: Araç kutusunu kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295602"
---
# <a name="using-the-toolbox"></a>Araç Kutusunu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projenize denetim ve diğer öğeleri eklemek için araç kutusunu kullanabilirsiniz. Kullanmakta olduğunuz ve yeniden boyutlandırma ve yerleştirmenize Tasarımcı yüzeyine başka denetimler sürükleyip bırakabilirsiniz.

 Araç kutusu, bir XAML dosyasının Tasarımcı görünümü gibi tasarımcı görünümleriyle birlikte görüntülenir. Araç kutusu yalnızca geçerli tasarımcıda kullanılabilecek denetimleri görüntüler.

 Projenizin hedeflediği .NET Framework sürümü araç kutusunda görünen denetim kümesini de etkiler. Varsayılan olarak, [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] projeler .NET Framework 4.5.1 hedefleyin. **Çözüm Gezgini**' de proje düğümünü seçip **Özellikler/uygulama/hedef çerçevesine**göz atarak, projenizi .NET Framework farklı bir sürümünü hedefleyecek şekilde ayarlayabilirsiniz.

## <a name="managing-the-toolbox-and-its-controls"></a>Araç kutusunu ve denetimlerini yönetme
 Varsayılan olarak, araç kutusu Visual Studio IDE 'nin sol tarafında daraltılır ve imleç onun üzerine taşındığında görüntülenir. Araç kutusunu sabitleyebilir (araç kutusu araç çubuğundaki **sabitleme** simgesine tıklayarak) imleci taşıdığınızda açık kalması gerekir. Ayrıca araç kutusu penceresini çıkarabilir ve ekranınızdaki herhangi bir yere sürükleyebilirsiniz. Araç kutusu araç çubuğuna sağ tıklayıp seçeneklerden birini seçerek araç kutusunu sabitleyebilir, çıkarabilir ve gizleyebilirsiniz.

 Bağlam menüsünde aşağıdaki komutları kullanarak bir araç kutusu sekmesindeki öğeleri yeniden düzenleyebilir veya özel sekmeler ve öğeler ekleyebilirsiniz:

- **Öğeyi yeniden adlandır** -seçili öğeyi yeniden adlandırır.

- **Tümünü Göster** -tüm olası denetimleri (geçerli Tasarımcı için geçerli olanları değil) gösterir.

- **Liste görünümü** -denetimleri dikey listesini gösterir. Denetimleri yatay olarak işaretlenmemişse, görünür.

- **Seç öğeleri** -açılır **araç kutusu öğelerini Seç** iletişim kutusunda görünen öğeler belirtebilirsiniz böylece **araç kutusu**. Göstermek veya seçerek ya da onay kutusunu temizleyerek bir öğeyi gizler.

- **Öğeleri alfabetik olarak Sırala** -öğeleri ada göre sıralar.

- **Araç çubuğunu Sıfırla** -varsayılan araç kutusu ayarlarını ve öğelerini geri yükler.

- **Sekme Ekle** -yeni bir araç kutusu sekmesi ekler.

- **Yukarı Taşı** -seçili öğeyi yukarı taşır.

- **Aşağı Taşı** -seçili öğeyi aşağı taşır.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Özel araç kutusu denetimleri oluşturma ve dağıtma
 Visual Basic veya görselde C#özel bir araç kutusu denetimi oluşturabilirsiniz ve [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) ya da [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)dayalı bir proje şablonuyla başlayabilirsiniz. Daha sonra denetiminizi, [araç kutusu denetimleri yükleyicisi](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)' ni kullanarak takım mateklarına dağıtabilir veya Web 'de yayımlayabilirsiniz.
