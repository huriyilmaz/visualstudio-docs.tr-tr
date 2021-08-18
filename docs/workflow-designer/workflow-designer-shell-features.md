---
title: İş Akışı Tasarımcısı Kabuk Özellikleri
description: İş Akışı Tasarımcısı kabuğu özelliklerinin, geçerli görünümü yönetmek için çeşitli düğmeler içerdiğini öğrenin.
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
ms.openlocfilehash: cca5d41db47c2cc59bd36f7114395f86ccb057ee4c251419130763a30bfc91f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440272"
---
# <a name="workflow-designer-shell-features"></a>İş Akışı Tasarımcısı Kabuk Özellikleri

İş Akışı Tasarımcısı üç ana kullanıcı arabirimi alandan oluşur: tasarımcı yüzeyi, yukarıdaki içerik haritası çubuğu ve bunun altındaki Kabuk. Ekranın en üstünde konumlandırılmış olan içerik haritası çubuğu, geçerli kök etkinliğin üst öğelerinin listesini göstermek için kullanılır. Daha fazla bilgi için bkz. [nasıl yapılır: Içerik Haritası gezintisini kullanma](../workflow-designer/how-to-use-breadcrumb-navigation.md). Ekranın ortasında konumlandırılmış olan tasarımcı yüzeyi iş akışları oluşturmak için kullanılır. Ekranın alt kısmında konumlandırılmış olan kabuk, geçerli görünümü yönetmek için bir dizi düğme içerir.

## <a name="shell-features"></a>Kabuk özellikleri
 Kabuğun sağ tarafında, iş akışınızı yakınlaştırmak veya uzaklaştırmak için kullanabileceğiniz düğmeler bulunur, iş akışınızın içeriğini Ekranınızın boyutuna uydurun ve genel bakış haritasını gösterebilir veya gizleyebilirsiniz. Ayrıca, CTRL + + ve CTRL +-klavye kısayollarını kullanarak bir iş akışını da yakınlaştırıp dışına taşıyabilirsiniz.

## <a name="overview-map"></a>Genel Bakış Haritası
 Genel Bakış Haritası, tüm alt öğeleri ve tüm genişletilmiş alt öğeleri dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinliğin küçük bir sürümünü görüntüler. Şu anda düzenleyici içinde görüntülenen etkinliğin bölümünü vurgulayan turuncu kenarlığı olan bir görünüm penceresi bulunur. Dikdörtgeni genel bakış haritasının etrafında sürüklemek, iş akışı tasarımcısını kaydırır ve düzenleyicinin görünümünü değiştirir.

> [!NOTE]
> İş Akışı Tasarımcısı Kullanıcı arabirimi sanallaştırılır. Etkinlik tasarımcıları yalnızca gerektiğinde işlenir. İş akışının bir kısmı tasarımcı yüzeyine hiç çizildiyse, bu bölüm genel bakış haritasında beyaz olarak görünür. Genel Bakış haritasının etrafında kaydırma, iş akışını tamamen çizer.

## <a name="copying-or-saving-workflows-as-images"></a>Iş akışlarını görüntü olarak kopyalama veya kaydetme
 İş akışları, bit eşlem biçiminde kopyalanabilir veya bit eşlem ya da vektör biçiminde kaydedilebilir. Bir görüntüyü kopyalama veya kaydetme, tüm alt öğeleri ve genişletilmiş alt öğelerinin tümünü başka bir programa dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinliğin bir görünümünü dışarı aktarmanın bir yolunu sağlar.

 Görüntü olarak kopyalamak için, Tasarımcıda herhangi bir yere sağ tıklayın ve **görüntü olarak Kopyala**' yı seçin. Görüntü olarak kaydetmek için, Tasarımcıda herhangi bir yere sağ tıklayın ve **görüntü olarak kaydet**' i seçin. İş akışları JPG, PNG, GIF veya XPS biçiminde kaydedilebilir. Biçim, pencerenin alt kısmındaki farklı **Kaydet:** açılan liste kutusunda bulunan **farklı kaydet** iletişim kutusunda seçilir.

## <a name="fonts-and-colors"></a>Yazı Tipleri ve Renkler

Visual Studio içinde İş Akışı Tasarımcısı kullanılan yazı tipleri, ortam yazı tipi tarafından denetlenir. İşletim sistemi temanız için yüksek karşıtlıklı bir renk düzeni kullanıyorsanız, İş Akışı Tasarımcısı içinde görüntülenen renkler değişir. değişiklikler İş Akışı Tasarımcısı etkin hale gelmeden önce yazı tipi veya renk ayarlarında değişiklik yaptıktan sonra Visual Studio yeniden başlatmanız gerekir.