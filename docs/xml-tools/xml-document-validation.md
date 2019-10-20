---
title: XML düzenleyicisinde XML belgesi doğrulaması
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c4133268f2e07753ab7ecd276bf92712484e9f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604054"
---
# <a name="xml-document-validation"></a>XML belgesini doğrulama

XML Düzenleyicisi, XML 1,0 söz dizimini denetler ve ayrıca siz yazarken veri doğrulaması gerçekleştirir. Düzenleyici bir belge türü tanımı (DTD) veya şema kullanarak doğrulayabilir. Kırmızı dalgalı alt çizgiler, XML 1,0 düzgün biçimlendirilmiş hataları vurgular. Mavi dalgalı alt çizgiler, DTD veya şema doğrulamasına göre anlam hataları gösterir. Her hatanın hata listesinde ilişkili bir girişi vardır. Fareyi dalgalı alt çizginin üzerinde duraklatarak hata mesajını da görüntüleyebilirsiniz.

Doğrulamada kullanılan şemalar, derlenmiş bir şemanın `targetNamespace` öğenin xmlns bildirimiyle eşleştirerek bulunur. Derlenmiş şemalar, öncelik sırasına göre listelenen aşağıdaki konumlardan birinden yüklenir:

- Belge **özellikleri** penceresinin **şemalar** alanında belirtilen dosya adından.

- Satır içi şema veya DTD.

- Dış DTD veya `xsd:schemaLocation` ve `xsd:noNamespaceSchemaLocation` özniteliği

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

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)