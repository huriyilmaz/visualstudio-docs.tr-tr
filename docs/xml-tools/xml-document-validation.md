---
title: XML düzenleyicisinde XML belgesi doğrulaması
description: XML düzenleyicisinde XML belge doğrulaması hakkında bilgi edinin ve XML 1,0 sözdizimini nasıl denetleyeceğinizi ve siz yazarken veri doğrulama işlemini nasıl gerçekleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/16/2021
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1dc2fcbbac33fe19cd50b44675609f7121c1be69
ms.sourcegitcommit: da5efd7698e357c59ba9b7dbbcaaceb5d1cfade2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128307057"
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

## <a name="entity-reference-limit"></a>Varlık başvuru sınırı
DTD işleme, varsayılan olarak 10.000 başvuru olarak varlık başvuruları sayısını kısıtlar ve çoğu XML şemasına uyum sağlayabilir.  Visual Studio içindeki hata iletisi "dosya adı için varlık başvuruları sınırı" değerini okuyabilir.

bir XML belgesini işlerken bu kısıtlamayla karşılaşırsanız ve doğrulayıcısı daha büyük bir şemaya genişletmek istiyorsanız, bu, `MaxNumberOfDtdEntityReferences` Visual Studio kayıt defteri anahtarı ile değiştirilebilir. bu değişikliği yapma hakkında daha fazla bilgi için bkz. [Visual Studio örneği için kayıt defterini düzenlemeyle](../install/tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance) . Bunun, bu makinede Kullanıcı tarafından açılan tüm XML belgeleri için geçerli olduğunu lütfen unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
