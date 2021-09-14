---
title: seçenekler, Windows Form Tasarımcısı, veri uı özelleştirmesi
description: Veri kaynakları penceresinde öğelerin kullanılabilir denetimleri listesinde hangi denetimlerin göründüğünü tanımlamak için veri UI özelleştirmesi sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6e419f144b44076e1108988cf1123a6a87b410ea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628623"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>seçenekler iletişim kutusu: Windows Form Tasarımcısı > veri kullanıcı arabirimi özelleştirmesi

Bu iletişim kutusu, veri kaynakları penceresinde öğelerin kullanılabilir denetimleri listesinde hangi denetimlerin göründüğünü tanımlar. açmak için **araçlar**  >  **seçenekler**' i seçin ve ardından **Windows Form Tasarımcısı**  >  **veri uı özelleştirmesi**' nı seçin.

bir Windows Forms uygulamasındaki form üzerine sürüklemeden önce veri kaynakları penceresinde bir öğeden denetim seçebilirsiniz. Kullanılabilir denetimler öğenin veri türüne göre belirlenir. Her veri türü, varsayılan bir denetim dahil olmak üzere, bu iletişim kutusunda tanımlanan geçerli ilişkili denetimlerin bir listesini içerir. Bir öğeyi veri kaynakları penceresinden bir denetim seçmeden bir form üzerine sürüklediğinizde, seçili öğenin veri türü için varsayılan denetim forma eklenir.

Her veri türü için kullanılabilir denetimlerin onay kutularını seçip temizleyerek ilişkili denetimlerin listesini özelleştirin. Listeye bir denetim eklemek için, <xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> araç kutusuna ya da veri bağlama özniteliğini uygulayan bir denetim ekleyin. Daha sonra Denetim, veri türü için denetim listesinde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: veri kaynakları penceresine özel denetimler ekleme](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Veri türü

Denetimleri ilişkilendirdiğiniz türlerin bir listesini görüntüler. Tablolar veri türü olarak temsil edilir `[List]` . Sütunlar, temel alınan veri deposundaki sütunun gerçek veri türü olarak gösterilir.

## <a name="associated-controls"></a>İlişkili denetimler

Seçili veri türüyle ilişkili denetimlerin listesini görüntüler. İlişkilendirmek veya ilişkiyi kaldırmak için denetimin yanındaki onay kutusunu işaretleyin veya temizleyin. Seçili denetimler, ilişkili veri türüne bağlanan bir veritabanı sütunu için veri kaynakları penceresinde görünür.

## <a name="set-default"></a>Varsayılan Yap’ı seçin

Seçili denetim türünü seçili veri türü için varsayılan değer olacak şekilde atar. Varsayılan denetim, veri kaynakları penceresinde bir veritabanı sütunu için kısayol menüsünde ilk seçim olarak görünür. Bir öğeyi veri kaynakları penceresinden bir denetim seçmeden bir form üzerine sürüklediğinizde, seçili öğenin veri türü için varsayılan denetim forma eklenir.

Bir veri türü için yalnızca bir denetim türü varsayılan olarak atanabilir.

## <a name="clear-default"></a>Varsayılanı Temizle

Bir denetimin atamasını seçili veri türü için varsayılan olarak kaldırır. Seçili veri türü için varsayılan değer yoksa, `[None]` Bu türdeki bir veritabanı sütunu için kısayol menüsünde ilk seçim olarak görünür.
