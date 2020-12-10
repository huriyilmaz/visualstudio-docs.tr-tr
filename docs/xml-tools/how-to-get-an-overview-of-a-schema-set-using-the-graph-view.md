---
title: Şema kümesine genel bakış elde etme
description: "XML şema Tasarımcısı: bir şema kümesindeki düğümlerin ve düğümler arasındaki ilişkilerin üst düzey bir görünümünü görmek için XML şema Gezgini 'nde grafik görünümünü nasıl kullanacağınızı öğrenin."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 699167f8fe3662bbb162706f3f9fc6e5d53d82dc
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995297"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Nasıl yapılır: grafik görünümünü kullanarak bir şema kümesine genel bakış alma

Bu konu başlığı altında, bir şema kümesindeki düğümlerin üst düzey bir görünümünü ve düğümler arasındaki ilişkileri görmek için [Graf görünümünün](../xml-tools/graph-view.md) nasıl kullanılacağı açıklanmaktadır.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun ve dosyayı *relationships. xsd* olarak kaydedin.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyası bağlantısını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [örnek xml şeması: ilişkiler](../xml-tools/sample-xsd-file-relationships.md) ' ten kopyalayın ve varsayılan olarak yeni xsd dosyasına eklenen kodu değiştirmek için yapıştırın.

4. XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

5. **XSD araç çubuğundan** grafik görünümünü seçin.

6. **XML şema Gezgini** 'Nde **şema kümesi** düğümünü seçin ve grafiği grafik görünümünün yüzeyine sürükleyin. Tüm genel düğümleri ve ilişkileri olan düğümleri bağlayan okları görmeniz gerekir.

     ![Graf Görünümü](../xml-tools/media/relationshipingraphview.gif)

7. Tasarım yüzeyinde herhangi bir düğüme tıklayın ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Rick-tasarım yüzeyinde herhangi bir öğe düğümüne tıklayın ve XML örnek belgesini görmek için **örnek XML oluştur** ' u seçin.
