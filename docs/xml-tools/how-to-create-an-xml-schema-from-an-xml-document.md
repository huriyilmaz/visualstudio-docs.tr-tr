---
title: XML Şeması Oluşturma
description: XML belgesinde XML düzenleyicisini Visual Studio XML Şeması tanımlama dili (XSD) şeması oluşturmak için kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: eba93ba429394272402c89e427ad974d1c9eb0f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130214"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Nasıl yapılır: XML belgesinde XML şeması oluşturma

XML düzenleyicisi, xml belgelerinden bir XML Şeması tanımlama dili (XSD) şeması oluşturmanıza olanak sağlar. XML dosyası şemanın nasıl oluşturulacaklarını aşağıdaki şekilde belirler:

- XML belgesiyle ilişkilendirilmiş bir şema veya Belge Türü Tanımı (DTD) yoksa, XML belgesinde yer alan veriler yeni bir XML Şeması çıkarımk için kullanılır.

- XML belgesi ilişkili bir DTD içeriyorsa, dış DTD ve iç alt küme karşılık gelen bir XML Şemasına dönüştürülür.

- XML belgesi, Azaltılmış (XDR) XML-Data satır içi bir şema içeriyorsa, XDR şeması karşılık gelen bir XML Şemasına dönüştürülür.

Oluşturulan şemalar daha sonra XML dosyası için IntelliSense sağlamak için kullanılır.

Şema çıkarım altyapısı hakkında daha fazla bilgi için [bkz. XML şeması çıkarım.](/dotnet/standard/data/xml/inferring-an-xml-schema)

## <a name="to-create-an-xml-schema"></a>XML şeması oluşturmak için

1. Bir XML dosyasını Visual Studio.

2. Menü çubuğunda **XML** Şema  >  **Oluştur'a tıklayın.**

   XML dosyasında bulunan her ad alanı için bir XML Şeması belgesi oluşturulur ve açılır. Her şema geçici bir çeşitli dosya olarak açılır. Şemalar diske kaydedilebilir, projenize eklenebilir veya atılır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
