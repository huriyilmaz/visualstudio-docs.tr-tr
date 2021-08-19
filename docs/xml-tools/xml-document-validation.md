---
title: XML düzenleyicisinde XML belgesi doğrulaması
description: XML düzenleyicisinde XML belge doğrulaması hakkında bilgi edinin ve XML 1,0 sözdizimini nasıl denetleyeceğinizi ve siz yazarken veri doğrulama işlemini nasıl gerçekleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 19585e36094868cedad279f0f7b4d982647da1d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091831"
---
# <a name="xml-document-validation"></a>XML belgesini doğrulama

XML Düzenleyicisi, XML 1,0 söz dizimini denetler ve ayrıca siz yazarken veri doğrulaması gerçekleştirir. Düzenleyici bir belge türü tanımı (DTD) veya şema kullanarak doğrulayabilir. Kırmızı dalgalı alt çizgiler, XML 1,0 düzgün biçimlendirilmiş hataları vurgular. Mavi dalgalı alt çizgiler, DTD veya şema doğrulamasına göre anlam hataları gösterir. Her hatanın hata listesinde ilişkili bir girişi vardır. Fareyi dalgalı alt çizginin üzerinde duraklatarak hata mesajını da görüntüleyebilirsiniz.

Doğrulamada kullanılan şemalar, `targetNamespace` derlenmiş bir şemanın, öğenin xmlns bildirimiyle eşleşmesi ile bulunur. Derlenmiş şemalar, öncelik sırasına göre listelenen aşağıdaki konumlardan birinden yüklenir:

- Belge **özellikleri** penceresinin **şemalar** alanında belirtilen dosya adından.

- Satır içi şema veya DTD.

- Dış DTD veya `xsd:schemaLocation` and `xsd:noNamespaceSchemaLocation` özniteliği

- "X-Schema" XDR şema ad alanı URI 'SI.

Şema boş olmayan bir hedef ad alanına sahip olduğunda aşağıdaki ek konumlarda şemalar de bulunabilir:

- Şemayı içeren başka bir düzenleyici penceresi.

- Geçerli çözümde bir şema.

- Şema önbelleği dizininden bir şema.

## <a name="xslt-files"></a>XSLT dosyaları
XSLT dosyasını düzenlediğinizde, şema önbelleğinde bulunan *XSLT. xsd* dosyası doğrulama için kullanılır. Doğrulama hataları mavi dalgalı alt çizgiler olarak gösterilir. XSLT derleyicisindeki hatalar kırmızı dalgalı alt çizgiler olarak gösterilir.

## <a name="xml-schema-xsd-files"></a>XML şeması (XSD) dosyaları
Bir XML şema dosyası düzenlenirken, şema önbelleğinde bulunan *XSDSchema. xsd* dosyası doğrulama için kullanılır. Doğrulama hataları mavi dalgalı alt çizgiler olarak gösterilir. Tüm derleme hataları da kırmızı dalgalı alt çizgilerle gösterilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
