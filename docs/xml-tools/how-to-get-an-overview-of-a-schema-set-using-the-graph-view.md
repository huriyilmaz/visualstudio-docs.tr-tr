---
title: Şema kümesine genel bakış elde etme
description: 'xml şema tasarımcısı: bir şema kümesindeki düğümlerin üst düzey bir görünümünü ve düğümler arasındaki ilişkileri görmek için, xml şema gezgininde Graph görünümünü nasıl kullanacağınızı öğrenin.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1461653dff8e757ec462a3d47eb76ba7ed4f0ed5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135084"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>nasıl yapılır: Graph görünümünü kullanarak bir şema kümesine genel bakış alma

bu konu başlığı altında, bir şema kümesindeki düğümlerin üst düzey bir görünümünü ve düğümler arasındaki ilişkileri görmek için [Graph görünümünün](../xml-tools/graph-view.md) nasıl kullanılacağı açıklanmaktadır.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun ve dosyayı *relationships. xsd* olarak kaydedin.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyası bağlantısını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [örnek xml şeması: ilişkiler](../xml-tools/sample-xsd-file-relationships.md) ' ten kopyalayın ve varsayılan olarak yeni xsd dosyasına eklenen kodu değiştirmek için yapıştırın.

4. XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

5. **XSD araç çubuğundan** Graph görünümünü seçin.

6. **XML şema gezgini** 'nde **şema kümesi** düğümünü seçin ve Graph görünümün yüzeyine sürükleyin. Tüm genel düğümleri ve ilişkileri olan düğümleri bağlayan okları görmeniz gerekir.

     ![Graf Görünümü](../xml-tools/media/relationshipingraphview.gif)

7. Tasarım yüzeyinde herhangi bir düğüme tıklayın ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Rick-tasarım yüzeyinde herhangi bir öğe düğümüne tıklayın ve XML örnek belgesini görmek için **örnek XML oluştur** ' u seçin.
