---
title: Şema kümesine genel bakış elde etme
description: "XML Şema Tasarımcısı: Bir şema kümesinde düğümlerin üst düzey bir görünümünü ve düğümler arasındaki ilişkileri görmek için XML Şema Gezgini'nde Graph Görünümünü kullanmayı öğrenin."
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
ms.openlocfilehash: a6168ca38de71d393d0a966a03d5172a515bf21721affe782d94ba6118c2c204
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121266928"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Nasıl: Graph View kullanarak bir şema kümesine genel bakış elde etmek

Bu konuda, bir [şema kümesinde düğümlerin üst](../xml-tools/graph-view.md) düzey bir görünümünü ve düğümler arasındaki ilişkileri görmek için Graph Görünümü'nin nasıl kullanımı açıklanmıştır.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve kök öğeyi İçerik Modeli Görünümünde görüntülemek için

1. Yeni bir XML Şeması dosyası oluşturun ve dosyayı *Relationships.xsd olarak kaydedin.*

2. Başlangıç **Görünümü'nde temel XML Şeması dosyasını görüntülemek ve düzenlemek için XML** düzenleyicisini kullan bağlantısına tıklayın.

3. Örnek XML [şeması:](../xml-tools/sample-xsd-file-relationships.md) ilişkiler'den XML Şeması örnek kodunu kopyalayın ve yeni XSD dosyasına varsayılan olarak eklenen kodu değiştirmek için yapıştırın.

4. XML düzenleyicisinde herhangi bir yere sağ tıklayın ve öğesini **Görünüm Tasarımcısı.**

5. XSD araç Graph **Görünüm'leri seçin.**

6. XML **Şema Gezgini'nde** **Şema Kümesi düğümünü** seçin ve düğümü Graph Görünümü'nde tasarım yüzeyine sürükleyin. İlişkili düğümleri bağlayan tüm genel düğümleri ve okları görüyor gerekir.

     ![Graf Görünümü](../xml-tools/media/relationshipingraphview.gif)

7. Tasarım yüzeyinde herhangi bir düğüme tıklayın ve seçilen düğümün şema kümesinde nerede olduğunu görmek için iş yüzeyi çubuğuna bakın.

8. Rick tasarım yüzeyindeki herhangi bir öğe düğümüne tıklayın ve XML örneği **belgesini görmek için** Örnek XML Oluştur'u seçin.
