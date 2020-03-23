---
title: Seçenekler, Windows Forms Designer, Veri UI Özelleştirme
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114684"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Seçenekler iletişim kutusu: Windows Forms Designer > Veri Kullanıcı Arama Birimi Özelleştirme

Bu iletişim kutusu, Veri Kaynakları penceresindeki öğeler için kullanılabilir denetimler listesinde hangi denetimlerin göründüğünü tanımlar. Açmak için **Araçlar** > **Seçenekleri'ni**seçin ve ardından Windows Forms **Designer** > **Data UI Özelleştirme'yi**seçin.

Bir Windows Forms uygulamasında forma sürüklemeden önce Veri Kaynakları penceresindeki bir öğeden denetim seçebilirsiniz. Kullanılabilir denetimler maddenin veri türüne göre belirlenir. Her veri türü, varsayılan denetim de dahil olmak üzere bu iletişim kutusunda tanımlandığı gibi geçerli ilişkili denetimlerin bir listesi vardır. Bir öğeyi Veri Kaynakları penceresinden denetim seçmeden bir forma sürüklediğinizde, seçili öğenin veri türü için varsayılan denetim forma eklenir.

Her veri türü için kullanılabilir denetimlerin onay kutularını seçip temizleyerek ilişkili denetimlerin listesini özelleştirin. Listeye denetim eklemek için, Araç Kutusu'na <xref:System.ComponentModel.DefaultBindingPropertyAttribute> veya <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> veri bağlama özniteliğini uygulayan bir denetim ekleyin. Denetim daha sonra veri türü denetimleri listesinde görünür. Daha fazla bilgi için [bkz: Veri Kaynakları penceresine Özel Denetimler Ekleyin.](../..//data-tools/add-custom-controls-to-the-data-sources-window.md)

## <a name="data-type"></a>Veri türü

Denetimleri ilişkilendirdiğiniz türlerin listesini görüntüler. Tablolar `[List]` veri türü olarak temsil edilir. Sütunlar, alttaki veri deposundaki sütunun gerçek veri türü olarak temsil edilir.

## <a name="associated-controls"></a>İlişkili denetimler

Seçili veri türüyle ilişkili denetimlerin listesini görüntüler. Denetimi ilişkilendirmek veya ilişkilendirmek için denetimin yanındaki onay kutusunu seçin veya temizleyin. Seçili denetimler, ilişkili veri türüne bağlı bir veritabanı sütunu için Veri Kaynakları penceresinde görünür.

## <a name="set-default"></a>Varsayılan Yap’ı seçin

Seçili denetim türünü seçili veri türü için varsayılan olarak atar. Varsayılan denetim, Veri Kaynakları penceresindeki bir veritabanı sütunu için kısayol menüsündeki ilk seçim olarak görünür. Bir öğeyi Veri Kaynakları penceresinden denetim seçmeden bir forma sürüklediğinizde, seçili öğenin veri türü için varsayılan denetim forma eklenir.

Bir veri türü için varsayılan olarak yalnızca bir denetim türü atanabilir.

## <a name="clear-default"></a>Varsayılanı Temizle

Seçili veri türü için varsayılan olarak denetim in atasını kaldırır. Seçili veri türü için varsayılan `[None]` yoksa, bu tür bir veritabanı sütununun kısayol menüsündeki ilk seçim olarak görünür.
