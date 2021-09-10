---
title: İş Akışı Tasarımcısı Kabuk Özellikleri
description: İş Akışı Tasarımcısı Shell özelliklerinin geçerli görünümü yönetmek için çeşitli düğmeler içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: f655a80fd25d7cf8e1f9fefdf329f62319cbc842
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963779"
---
# <a name="workflow-designer-shell-features"></a>İş Akışı Tasarımcısı Kabuk Özellikleri

İş Akışı Tasarımcısı üç ana kullanıcı arabirimi alanı vardır: tasarımcı yüzeyi, üzerindeki İçerik yüzeyi çubuğu ve altındaki kabuk. Ekranın üst kısmında yer alan breadcrumb çubuğu, geçerli kök etkinliğin üstlerinin listesini görüntülemek için kullanılır. Daha fazla bilgi için, [bkz. How to: Use Breadcrumb Navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). İş akışlarını oluşturmak için, ekranın merkezine konumlenmiş tasarımcı yüzeyi kullanılır. Ekranın alt kısmında yer alan kabuk, geçerli görünümü yönetmek için bir dizi düğme içerir.

## <a name="shell-features"></a>Kabuk Özellikleri
 Kabuğun sağ tarafında, iş akışınızı yakınlaştırmak veya uzaklaştırmak, iş akışı içeriğinizi ekran boyutuna sığdırmak ve genel bakış haritasını göstermek veya gizlemek için kullanabileceğiniz düğmeler bulunur. CTRL++ ve CTRL+- klavye kısayollarını kullanarak bir iş akışını yakınlaştırabilir veya uzaklaştırabilirsiniz.

## <a name="overview-map"></a>Genel Bakış Haritası
 Genel bakış haritası, tüm öğeleri ve genişletilmiş tüm öğeleri de dahil olmak üzere geçerli iş haritası kökünde etkinliğin tamamının küçük bir sürümünü görüntüler. Düzenleyicide şu anda görüntülenen etkinliğin bölümünü vurgulayan turuncu kenarlıklı bir dikdörtgen olan bir görünüm açısı vardır. Dikdörtgeni genel bakış haritasının etrafına sürüklemek, iş akışı tasarımcısını kaydırarak düzenleyicinin görünümünü değiştirir.

> [!NOTE]
> Bu İş Akışı Tasarımcısı arabirimi sanallaştırıldı. Etkinlik tasarımcıları yalnızca gerektiğinde işlenir. İş akışının bir kısmı tasarımcı yüzeyinde hiç çizilmse, bu kısım genel bakış haritasında beyaz olarak görünür. Genel bakış haritasının etrafında kaydırmak iş akışını tamamen çizer.

## <a name="copying-or-saving-workflows-as-images"></a>İş Akışlarını Görüntü Olarak Kopyalama veya Kaydetme
 İş akışları bit eşlem biçiminde kopyalanamaz veya bit eşlem veya vektör biçiminde kaydedilebilir. Bir görüntüyü kopyalama veya kaydetme, tüm diğer ve genişletilmiş çocuklar da dahil olmak üzere geçerli breadcrumb kökünde etkinliğin tamamının görünümünü dışarı aktarmanın bir yolunu sağlar.

 Görüntü olarak kopyalamak için tasarımcının herhangi bir yerine sağ tıklayın ve Görüntü Olarak **Kopyala'yı seçin.** Görüntü olarak kaydetmek için tasarımcının herhangi bir yerine sağ tıklayın ve Görüntü Olarak **Kaydet'i seçin.** İş akışları JPG, PNG, GIF veya XPS biçiminde kaydedilebilir. Biçim, pencerenin en altındaki **Tür:**  açılan liste kutusundaki Farklı Kaydet iletişim kutusunda seçilidir.

## <a name="fonts-and-colors"></a>Yazı Tipleri ve Renkler

Ortamın içinde İş Akışı Tasarımcısı yazı Visual Studio ortam yazı tipi tarafından denetlenmektedir. İşletim sistemi İş Akışı Tasarımcısı yüksek karşıtlıklı bir renk düzeni kullanıyorsanız, bu renk düzeninde görüntülenen renkler değişir. Yazı tipi Visual Studio renk ayarlarında değişiklik olduktan sonra, değişiklikler yazı tipinde etkin hale gelmeden önce bu ayarları yeniden İş Akışı Tasarımcısı.