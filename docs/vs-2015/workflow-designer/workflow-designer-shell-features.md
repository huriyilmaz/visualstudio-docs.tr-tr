---
title: İş Akışı Tasarımcısı Shell özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606594"
---
# <a name="workflow-designer-shell-features"></a>İş Akışı Tasarımcısı Kabuk Özellikleri
[!INCLUDE[wfd1](../includes/wfd1-md.md)] üç ana kullanıcı arabirimi alanlarından oluşur: tasarımcı yüzeyi, yukarıdaki içerik haritası çubuğu ve bunun altındaki Kabuk. Ekranın en üstünde konumlandırılmış olan içerik haritası çubuğu, geçerli kök etkinliğin üst öğelerinin listesini göstermek için kullanılır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Nasıl yapılır: Içerik Haritası gezintisi kullanma](../workflow-designer/how-to-use-breadcrumb-navigation.md). Ekranın ortasında konumlandırılmış olan tasarımcı yüzeyi iş akışları oluşturmak için kullanılır. Ekranın alt kısmında konumlandırılmış olan kabuk, geçerli görünümü yönetmek için bir dizi düğme içerir.

## <a name="shell-features"></a>Kabuk özellikleri
 Kabuğun sağ tarafında, iş akışınızı yakınlaştırmak veya uzaklaştırmak için kullanabileceğiniz düğmeler bulunur, iş akışınızın içeriğini Ekranınızın boyutuna uydurun ve genel bakış haritasını gösterebilir veya gizleyebilirsiniz. Ayrıca, CTRL + + ve CTRL +-klavye kısayollarını kullanarak bir iş akışını da yakınlaştırıp dışına taşıyabilirsiniz.

## <a name="overview-map"></a>Genel Bakış Haritası
 Genel Bakış Haritası, tüm alt öğeleri ve tüm genişletilmiş alt öğeleri dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinliğin küçük bir sürümünü görüntüler. Şu anda düzenleyici içinde görüntülenen etkinliğin bölümünü vurgulayan turuncu kenarlığı olan bir görünüm penceresi bulunur. Dikdörtgeni genel bakış haritasının etrafında sürüklemek, iş akışı tasarımcısını kaydırır ve düzenleyicinin görünümünü değiştirir.

> [!NOTE]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)]Kullanıcı arabirimi sanallaştırılır. Etkinlik tasarımcıları yalnızca gerektiğinde işlenir. İş akışının bir kısmı tasarımcı yüzeyine hiç çizildiyse, bu bölüm genel bakış haritasında beyaz olarak görünür. Genel Bakış haritasının etrafında kaydırma, iş akışını tamamen çizer.

## <a name="copying-or-saving-workflows-as-images"></a>Iş akışlarını görüntü olarak kopyalama veya kaydetme
 İş akışları, bit eşlem biçiminde kopyalanabilir veya bit eşlem ya da vektör biçiminde kaydedilebilir. Bir görüntüyü kopyalama veya kaydetme, tüm alt öğeleri ve genişletilmiş alt öğelerinin tümünü başka bir programa dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinliğin bir görünümünü dışarı aktarmanın bir yolunu sağlar.

 Görüntü olarak kopyalamak için, Tasarımcıda herhangi bir yere sağ tıklayın ve **görüntü olarak Kopyala**' yı seçin. Görüntü olarak kaydetmek için, Tasarımcıda herhangi bir yere sağ tıklayın ve **görüntü olarak kaydet**' i seçin. İş akışları JPG, PNG, GIF veya XPS biçiminde kaydedilebilir. Biçim, pencerenin alt kısmındaki farklı **Kaydet:** açılan liste kutusunda bulunan **farklı kaydet** iletişim kutusunda seçilir.

## <a name="fonts-and-colors"></a>Yazı Tipleri ve Renkler
 İçinde kullanılan yazı tipleri [!INCLUDE[wfd2](../includes/wfd2-md.md)] , [!INCLUDE[vs2010](../includes/vs2010-md.md)] ortam yazı tipi tarafından denetlenir. [!INCLUDE[wfd2](../includes/wfd2-md.md)]İşletim sistemi temanız için yüksek karşıtlık renk düzeni kullanıyorsanız, değişiklik içinde görüntülenen renkler. [!INCLUDE[vs2010](../includes/vs2010-md.md)]Değişikliklerin etkili olabilmesi için yazı tipinde veya renk ayarlarında bir değişiklik yaptıktan sonra yeniden başlatmanız gerekir [!INCLUDE[wfd2](../includes/wfd2-md.md)] .