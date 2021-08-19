---
title: 'Nasıl Yapılır: XML Dosyalarını Düzenleme'
ms.date: 11/04/2016
description: xml veya DTD içeriğini içeren dosyaları düzenlemek için Visual Studio 'de xml düzenleyicisini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d308fa0298297bf91313f611bc0efe791191f9ae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114491"
---
# <a name="how-to-edit-xml-files"></a>Nasıl yapılır: XML dosyalarını düzenleme

XML Düzenleyicisi, XML dosyaları için yeni düzenleyicidir. tek başına bir XML dosyasında veya Visual Studio projesiyle ilişkili bir dosyada kullanılabilir. XML Düzenleyicisi şu dosya uzantılarıyla ilişkili: *.config*, *. dtd*, *.xml*, *. xsd*, *. xdr*, *. xsl*, *. XSLT* ve *. vssettings*. XML Düzenleyicisi Ayrıca, kayıtlı belirli bir düzenleyici bulunmayan ve XML veya DTD içeriği içeren başka herhangi bir dosya türü ile ilişkilendirilir.

> [!NOTE]
> XHTML belgeleri HTML Düzenleyicisi tarafından işlenir.

Bir XML dosyasını düzenlemek için, düzenlemek istediğiniz dosyayı açın.

## <a name="add-a-new-xml-file-to-a-project"></a>Projeye yeni bir XML dosyası ekleyin

1. **Project** menüsünden **yeni öğe ekle**' yi seçin.

2. **Şablonlar** bölmesinden **XML dosyası** ' nı seçin.

3. **Ad** alanına dosya adını girin ve **Ekle**' ye basın.

   XML dosyası projeye eklenir ve XML düzenleyicisinde açılır. Dosya varsayılan XML bildirimini içerir, `<?xml version="1.0" encoding="utf-8" ?>` .

## <a name="add-an-existing-xml-file-to-a-project"></a>Bir projeye var olan bir XML dosyası Ekle

1. **Project** menüsünde **varolan öğe ekle**' yi seçin.

   **Varolan öğe Ekle** iletişim kutusu görüntülenir.

2. Bir XML dosyası seçin ve **Ekle**'ye basın.

## <a name="create-a-new-xml-or-xslt-file"></a>Yeni bir XML veya XSLT dosyası oluşturma

1. **Dosya** menüsünde **Yeni**' yi seçin.

   **Yeni dosya** iletişim kutusu görüntülenir.

2. Yeni bir XML dosyası oluşturmak için **XML dosyasını** seçin; veya yeni bir XSLT stil sayfası oluşturmak için **XSLT dosyası** ' nı seçin.

3. **Aç**’ı seçin.

## <a name="create-an-empty-project-for-xml-files"></a>XML dosyaları için boş bir proje oluştur

::: moniker range="vs-2017"

1. **dosya** menüsünden **yeni** > **Project**' yi seçin.

   **Yeni Proje** iletişim kutusu görünür.

2. seçtiğiniz kod dilini seçin ve **boş Project (.NET Framework)** şablonunu seçin.

3. **Tamam**’ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. **dosya** menüsünden **yeni** > **Project**' yi seçin.

2. şablon arama kutusuna **boş Project** girin, **boş Project (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

3. **Oluştur**’u seçin.

::: moniker-end

4. Projeye XML dosyaları ekleyin.

   XML Düzenleyicisi, bu projeye eklediğiniz şemaları bulur ve bu proje açıkken düzenlediğiniz XML, şema veya XSLT dosyalarında doğrulama ve IntelliSense için kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
- [XML belgesi özellikleri, Özellikler penceresi](../xml-tools/xml-document-properties-properties-window.md)
- [Nasıl yapılır: XML belgesinden XML şeması oluşturma](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
