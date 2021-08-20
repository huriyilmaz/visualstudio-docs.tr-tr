---
title: Seçenekler, Windows Forms Tasarımcısı, Veri Kullanıcı Arabirimi Özelleştirmesi
description: Veri Kaynakları penceresindeki öğeler için kullanılabilir denetimler listesinde hangi denetimlerin görüntül olduğunu tanımlamak için Veri Kullanıcı Arabirimi Özelleştirmesi sayfasını kullanmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151190"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Seçenekler iletişim kutusu: Windows Form Tasarımcısı > Kullanıcı Arabirimi Özelleştirmesi

Bu iletişim kutusu, Veri Kaynakları penceresindeki öğeler için kullanılabilir denetimler listesinde hangi denetimlerin görüntül olduğunu tanımlar. Açmak için Araçlar **Seçenekler'i ve**  >  **ardından** FormLar Windows **Kullanıcı Arabirimi**  >  **Özelleştirmesi'ne tıklayın.**

Bir denetimi, Windows Forms uygulamasında forma sürüklemeden önce Veri Kaynakları penceresinden bir öğeden seçebilirsiniz. Kullanılabilir denetimler öğenin veri türüne göre belirlenir. Her veri türü, varsayılan denetim de dahil olmak üzere bu iletişim kutusunda tanımlandığı gibi geçerli ilişkili denetimlerin bir listesine sahiptir. Veri Kaynakları penceresinden bir öğeyi bir denetim seçmeden bir forma sürüklerken, seçilen öğenin veri türü için varsayılan denetim forma eklenir.

Her veri türü için kullanılabilir denetimlerin onay kutularını seçerek ve temizerek ilişkili denetimlerin listesini özelleştirin. Listeye denetim eklemek için Araç Kutusuna veya veri bağlama özniteliğini <xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayan bir denetim ekleyin. Denetim daha sonra veri türü için denetim listesinde görünür. Daha fazla bilgi için, [bkz. How to: Add Custom Controls to the Data Sources window](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Veri türü

Denetimleri ilişkilendirmek istediğiniz türlerin listesini görüntüler. Tablolar veri türü olarak `[List]` temsil edildi. Sütunlar, temel alınan veri deposuna sütunun gerçek veri türü olarak temsil edilen.

## <a name="associated-controls"></a>İlişkili denetimler

Seçilen veri türüyle ilişkili denetimlerin listesini görüntüler. Denetimi ilişkilendirmek veya ilişkilendirmeyi silmek için denetimin yanındaki onay kutusunu seçin veya temizleyin. Seçili denetimler, ilişkili veri türüne bağlı bir veritabanı sütunu için Veri Kaynakları penceresinde görüntülenir.

## <a name="set-default"></a>Varsayılan Yap’ı seçin

Seçilen denetim türünü seçilen veri türü için varsayılan olarak atar. Varsayılan denetim, Veri Kaynakları penceresindeki veritabanı sütunu kısayol menüsünde ilk seçim olarak görünür. Veri Kaynakları penceresinden bir öğeyi bir denetim seçmeden bir forma sürüklerken, seçilen öğenin veri türü için varsayılan denetim forma eklenir.

Bir veri türü için varsayılan olarak yalnızca bir denetim türü atanabilir.

## <a name="clear-default"></a>Varsayılanı Temizle

Bir denetimin seçili veri türü için varsayılan olarak işaretlerini kaldırır. Seçili veri türü için varsayılan değer yoksa, bu tür bir veritabanı sütunu için kısayol menüsünde `[None]` ilk seçim olarak görünür.
