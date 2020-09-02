---
title: 'Nasıl yapılır: XML dosyalarını düzenleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670879"
---
# <a name="how-to-edit-xml-files"></a>Nasıl Yapılır: XML Dosyalarını Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi, XML dosyaları için yeni düzenleyicidir. Tek başına bir XML dosyasında veya Visual Studio projesiyle ilişkili bir dosyada kullanılabilir. XML Düzenleyicisi şu dosya uzantılarıyla ilişkili:. config,. dtd,. xml,. xsd,. xdr,. Xsl,. XSLT ve. vssettings. XML Düzenleyicisi Ayrıca, kayıtlı belirli bir düzenleyici bulunmayan ve XML veya DTD içeriği içeren başka herhangi bir dosya türü ile ilişkilendirilir.

> [!NOTE]
> XHTML belgeleri HTML Düzenleyicisi tarafından işlenir.

### <a name="to-edit-an-xml-file"></a>Bir XML dosyasını düzenlemek için

1. Düzenlemek istediğiniz dosyaya çift tıklayın.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Projeye yeni bir XML dosyası eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. **Şablonlar** bölmesinden **XML dosyası** ' nı seçin.

3. **Ad** alanına dosya adını girin ve **Ekle**' ye basın.

     XML dosyası projeye eklenir ve XML düzenleyicisinde açılır. Dosya varsayılan XML bildirimini içerir, `<?xml version="1.0" encoding="utf-8" ?>` .

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Bir projeye var olan bir XML dosyasını eklemek için

1. **Proje** menüsünden **Varolan öğe Ekle**' yi seçin.

     **Varolan öğe Ekle** iletişim kutusu görüntülenir.

2. Bir XML dosyası seçin ve **Ekle**'ye basın.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Yeni bir XML veya XSLT dosyası oluşturmak için

1. **Dosya** menüsünde **Yeni**' yi seçin.

     **Yeni dosya** iletişim kutusu görüntülenir.

2. Yeni bir XML dosyası oluşturmak için **XML dosyasını** seçin; veya yeni bir XSLT stil sayfası oluşturmak için **XSLT dosyası** ' nı seçin.

3. **Aç**’a tıklayın.

### <a name="to-create-a-project-for-xml-files"></a>XML dosyaları için bir proje oluşturmak için

1. **Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin.

     **Yeni Proje** iletişim kutusu görünür.

2. Seçtiğiniz kod dilini seçin, **boş proje**' yi seçin ve **Tamam**' ı tıklatın.

3. Projeye XML dosyaları ekleyin.

     XML Düzenleyicisi, bu projeye eklediğiniz şemaları bulur ve bu proje açıkken düzenlediğiniz XML, şema veya XSLT dosyalarında doğrulama ve IntelliSense için kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md) [XML belge özellikleri, Özellikler penceresi](../xml-tools/xml-document-properties-properties-window.md) [nasıl yapılır: bir XML belgesinden XML şeması oluşturma](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
