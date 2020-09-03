---
title: 'Nasıl yapılır: XSLT ile kesme noktaları kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656301"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Nasıl Yapılır: XSLT ile Kesme Noktaları Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir XSLT stil sayfasında veya XML kaynak belgesinde kesme noktaları ayarlayabilirsiniz. Bir etikette kesme noktası ayarlarsanız, yürütme başladığında kesme noktası kaynak satırı bilgilerine sahip bir sonraki ifadeye geçer.

 Daha fazla bilgi için bkz. [hata ayıklama temelleri: kesme noktaları](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Stil sayfasında kesme noktası ayarlama
 Bir XSLT stil sayfasının başlangıç etiketleri, bitiş etiketleri ve metin düğümleri üzerinde kesme noktaları ayarlanabilir. Kesme noktaları, bir betik bloğundaki kodda de ayarlanabilir.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Stil sayfasında bir kesme noktası ayarlamak için

1. XML düzenleyicisinde bir stil sayfası açın.

2. İmleci kesme noktası konumuna konumlandırın, sağ tıklayın, **kesme**noktası ' nın üzerine gelin ve **kesme noktası Ekle**' ye tıklayın.

3. Belge Özellikleri penceresinin **giriş** alanındaki gözata (**...**) düğmesine tıklayın.

4. XML kaynak belgesini bulun ve **Aç**' a tıklayın.

     Bu, XSLT dönüştürmesi için kullanılan kaynak belge dosyasını ayarlar.

5. XML Düzenleyicisi araç çubuğundaki **XSL hata ayıkla** düğmesine tıklayın.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>XML kaynak belgesinde kesme noktası ayarlama
 Kesme noktaları öğeler, öznitelikler, ad alanı düğümü, açıklamalar, işleme yönergesinde ve bir XML kaynak belgesinin metin düğümlerinde ayarlanabilir. Belge düğümünde veya üst öğeden devralınan bir ad alanı düğümünde bir kesme noktası ayarlayamazsınız.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Bir XML kaynak belgesinde bir kesme noktası ayarlamak için

1. XML belgesini XML düzenleyicisinde açın.

2. İmleci kesme noktası konumuna konumlandırın, sağ tıklayın, **kesme**noktası ' nın üzerine gelin ve **kesme noktası Ekle**' ye tıklayın.

3. Belge Özellikleri penceresinin **stil sayfası** alanındaki gözata (**...**) düğmesine tıklayın.

4. XML kaynak belgesini bulun ve **Aç**' a tıklayın.

     Bu, XSLT dönüştürmesi için kullanılan kaynak belge dosyasını ayarlar.

5. XML Düzenleyicisi araç çubuğundaki **XSL hata ayıkla** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek Yol: XSLT Stil Sayfasında Hata Ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
