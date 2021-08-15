---
title: XML düzenleyicisinde XML Belge Doğrulaması
description: XML düzenleyicisinde XML belge doğrulaması hakkında bilgi edinmek, XML 1.0 söz dizimi denetimi yapmayı ve siz yazarak veri doğrulamayı nasıl gerçekleştiriyor?
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
ms.openlocfilehash: 59fe8ee674bca836f25db75a828bbb807734e4b57e646b563570bae3355b766e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121242788"
---
# <a name="xml-document-validation"></a>XML belgesini doğrulama

XML düzenleyicisi XML 1.0 söz dizimi denetler ve siz yazarak veri doğrulamayı gerçekleştirir. Düzenleyici, belge türü tanımı (DTD) veya şema kullanarak doğrulanabilir. Kırmızı dalgalı alt çizgiler, XML 1.0 iyi oluşturulmuş hataları vurgular. Mavi dalgalı alt çizgiler DTD veya şema doğrulamasına dayalı semantik hataları gösterir. Her hatanın hata listesinde ilişkili bir girişi vardır. Ayrıca, fareyi dalgalı alt çizginin üzerine duraklatarak da hata iletisini görüntüebilirsiniz.

Doğrulamada kullanılan şemalar, derlenmiş bir `targetNamespace` şemanın öğesinin xmlns bildirimiyle eşleştirerek bulunur. Derlenmiş şemalar, öncelik sırasına göre listelenen aşağıdaki konumlardan biri tarafından yüklenir:

- Belge Özellikleri penceresinin **Şemalar** alanında belirtilen dosya **adı.**

- Satır içi şema veya DTD.

- Dış DTD veya `xsd:schemaLocation` ve `xsd:noNamespaceSchemaLocation` özniteliği

- Bir "x-schema" XDR şema ad alanı URI'si.

Şema boş olmayan bir hedef ad alanına sahip olduğunda şemalar aşağıdaki ek konumlarda da bulunabilir:

- Şemayı içeren başka bir düzenleyici penceresi.

- Geçerli çözümde bir şema.

- Şema önbelleği dizininden bir şema.

## <a name="xslt-files"></a>XSLT dosyaları
Bir XSLT dosyasını düzenlerken, doğrulama için şema önbelleğinde bulunan *xslt.xsd* dosyası kullanılır. Doğrulama hataları mavi dalgalı alt çizgi olarak gösterilir. XSLT derleyicisi hataları kırmızı dalgalı alt çizgi olarak gösterilir.

## <a name="xml-schema-xsd-files"></a>XML şeması (XSD) dosyaları
Bir XML Şema dosyasını düzenlerken, doğrulama için şema önbelleğinde bulunan *xsdschema.xsd* dosyası kullanılır. Doğrulama hataları mavi dalgalı alt çizgi olarak gösterilir. Derleme hataları kırmızı dalgalı alt çizgilerle de gösterilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
