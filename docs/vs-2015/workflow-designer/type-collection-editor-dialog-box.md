---
title: Tür koleksiyonu Düzenleyicisi Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670158"
---
# <a name="type-collection-editor-dialog-box"></a>Tür Koleksiyonu Düzenleyicisi İletişim Kutusu
**Tür koleksiyonu Düzenleyicisi** iletişim kutusu, bilinen türleri **gönderme** ve **alma** etkinliklerine eklemek için kullanılır. Bu iletişim kutusu, **InvokeMethod** etkinliğine genel tür bağımsız değişkenleri eklemek için de kullanılır. Bilinen türleri eklemek için **gönderme** ve **alma** etkinliği Için kullanıldığında, **tür koleksiyonu Düzenleyicisi** iletişim kutusu tür eklemeleri benzersiz olmasını gerektirir. Yinelenen bir tür eklenirse ve değişiklik **Tamam**' a tıklandıktan sonra, bir hata iletisi döndürülür. Genel tür bağımsız değişkenleri eklemek için **InvokeMethod** etkinliği kullanıldığında, **tür koleksiyonu Düzenleyicisi** iletişim kutusu yinelenen türlerin eklenmesine izin verir.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] bilinen türler, bkz. [veri sözleşmesi bilinen türleri](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 Aşağıdaki tabloda, **tür koleksiyonu** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|----------------|-----------------|
|**Tür Listesi**|Eklenmiş veya kaldırılmış türlerin listesi.|

## <a name="to-bring-up-the-type-collection-editor"></a>Tür koleksiyonu düzenleyicisini getirmek için

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Gönderme ve alma etkinlikleri için tür koleksiyonu düzenleyicisini getirmek için

1. Tasarım görünümünde **Gönder** veya **Al** etkinliğini seçin.

2. **Özellikler** penceresini açmak için **F4** tuşuna basın.

3. **Özellikler** penceresinde, **KnownTypes** özelliğinin yanındaki üç nokta düğmesine tıklayın.

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod etkinliğinin tür koleksiyonu düzenleyicisini açmak için

1. Tasarım görünümünde **InvokeMethod** etkinliğini seçin.

2. **Özellikler** penceresini açmak için **F4** tuşuna basın.

3. **Özellikler** penceresinde **genericTypeArguments** özelliğinin yanındaki üç nokta düğmesine tıklayın.