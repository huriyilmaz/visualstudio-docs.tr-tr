---
title: İş Akışı Tasarımcısı türü koleksiyon Düzenleyicisi Iletişim kutusu
description: Gönderme ve alma etkinliklerine bilinen türler eklemek için tür koleksiyon Düzenleyicisi iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: bfcd57fb13eebaec38bf5f478182e54af108b0c0
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963707"
---
# <a name="type-collection-editor-dialog-box"></a>Tür Koleksiyonu Düzenleyicisi İletişim Kutusu

**Tür koleksiyonu Düzenleyicisi** iletişim kutusu, bilinen türleri **gönderme** ve **alma** etkinliklerine eklemek için kullanılır. Bu iletişim kutusu, **InvokeMethod** etkinliğine genel tür bağımsız değişkenleri eklemek için de kullanılır. Bilinen türleri eklemek için **gönderme** ve **alma** etkinliği Için kullanıldığında, **tür koleksiyonu Düzenleyicisi** iletişim kutusu tür eklemeleri benzersiz olmasını gerektirir. Yinelenen bir tür eklenirse ve değişiklik **Tamam**' a tıklandıktan sonra, bir hata iletisi döndürülür. Genel tür bağımsız değişkenleri eklemek için **InvokeMethod** etkinliği kullanıldığında, **tür koleksiyonu Düzenleyicisi** iletişim kutusu yinelenen türlerin eklenmesine izin verir.

Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Aşağıdaki tabloda, **tür koleksiyonu** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|-|-----------------|
|**Tür Listesi**|Eklenmiş veya kaldırılmış türlerin listesi.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Gönderme ve alma etkinlikleri için tür koleksiyonu düzenleyicisini getirmek için

1. Tasarım görünümünde **Gönder** veya **Al** etkinliğini seçin.

2. **Özellikler** penceresini açmak için **F4** tuşuna basın.

3. **Özellikler** penceresinde, **KnownTypes** özelliğinin yanındaki üç nokta düğmesine tıklayın.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod etkinliğinin tür koleksiyonu düzenleyicisini açmak için

1. Tasarım görünümünde **InvokeMethod** etkinliğini seçin.

2. **Özellikler** penceresini açmak için **F4** tuşuna basın.

3. **Özellikler** penceresinde **genericTypeArguments** özelliğinin yanındaki üç nokta düğmesine tıklayın.
