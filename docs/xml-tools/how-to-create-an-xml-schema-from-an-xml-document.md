---
title: XML şeması oluşturma
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10ce1c6dc5bd24b391a8cde184a32684270662ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815454"
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

2. Menü çubuğunda, **XML**  >  **şeması oluştur**' u seçin.

   XML dosyasında bulunan her ad alanı için bir XML şeması belgesi oluşturulup açılır. Her şema geçici bir çeşitli dosya olarak açılır. Şemalar diske kaydedilebilir, projenize eklenebilir veya atılır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)
