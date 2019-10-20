---
title: 'Nasıl yapılır: XML belgesinden XML şeması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670936"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Nasıl yapılır: XML belgesinden XML şeması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi bir XML belgesinden XML şeması tanım dili (XSD) şeması oluşturmanıza olanak sağlar. XML örnek belgesi, şemanın nasıl oluşturulduğunu aşağıdaki şekilde belirler:

- XML belgesinde ilişkili bir şema veya belge türü tanımı (DTD) yoksa, XML belgesindeki veriler yeni bir XML şemasını çıkarsmak için kullanılır.

- XML belgesi ilişkili bir DTD içeriyorsa, dış DTD ve iç alt küme karşılık gelen bir XML şemasına dönüştürülür.

- XML belgesi satır içi XML verisi azaltılmış (XDR) şeması içeriyorsa, XDR şeması karşılık gelen bir XML şemasına dönüştürülür.

  Oluşturulan şemalar, XML belgesi için IntelliSense sağlamak üzere kullanılır.

  Şema çıkarımı altyapısı hakkında daha fazla bilgi için bkz. [XML şeması oluşturma](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Bir XML şeması oluşturmak için

1. XML düzenleyicisine bir XML örnek belgesi yükleyin.

2. **Araç çubuğundan** **şema oluştur** düğmesine tıklayın.

     XML örnek belgesinde bulunan her ad alanı için bir XML şeması belgesi oluşturulup açılır. Her şema geçici bir çeşitli dosya olarak açılır.

     Şemalar diske kaydedilebilir, projenize eklenebilir veya atılır.

    > [!NOTE]
    > **Şema oluştur** komutu ayrıca XML düzenleyicisinin kısayol menüsünde ve **XML** menüsü altında bulunur.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)
