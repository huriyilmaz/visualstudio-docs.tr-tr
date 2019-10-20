---
title: XML şeması oluşturma
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73563d732aab48192892794c15750bc9e5d3eb6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645959"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Nasıl yapılır: XML belgesinden XML şeması oluşturma

XML Düzenleyicisi bir XML belgesinden XML şeması tanım dili (XSD) şeması oluşturmanıza olanak sağlar. XML dosyası şemanın nasıl oluşturulduğunu aşağıdaki şekilde belirler:

- XML belgesinde ilişkili bir şema veya belge türü tanımı (DTD) yoksa, XML belgesindeki veriler yeni bir XML şemasını çıkarsmak için kullanılır.

- XML belgesi ilişkili bir DTD içeriyorsa, dış DTD ve iç alt küme karşılık gelen bir XML şemasına dönüştürülür.

- XML belgesi satır içi XML verisi azaltılmış (XDR) şeması içeriyorsa, XDR şeması karşılık gelen bir XML şemasına dönüştürülür.

Oluşturulan şemalar, XML dosyası için IntelliSense sağlamak üzere kullanılır.

Şema çıkarımı altyapısı hakkında daha fazla bilgi için bkz. [XML şemasını](/dotnet/standard/data/xml/inferring-an-xml-schema)çıkarma.

## <a name="to-create-an-xml-schema"></a>Bir XML şeması oluşturmak için

1. Visual Studio 'da bir XML dosyası açın.

2. Menü çubuğunda **XML**  > **şema oluştur**' u seçin.

   XML dosyasında bulunan her ad alanı için bir XML şeması belgesi oluşturulup açılır. Her şema geçici bir çeşitli dosya olarak açılır. Şemalar diske kaydedilebilir, projenize eklenebilir veya atılır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)