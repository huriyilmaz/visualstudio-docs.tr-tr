---
title: DebuggerDisplay özniteliği Ekle
description: Hata ayıklayıcı değişkeni penceresinin bir nesneyi, özelliği veya alanı nasıl görüntülediğini denetlemek için DebuggerDisplay özniteliğini nasıl ekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871125"
---
# <a name="add-debuggerdisplay-attribute"></a>DebuggerDisplay özniteliği Ekle

Bu kod üretimi için geçerlidir:

- C#

**Ne:** [DebuggerDisplay özniteliği](../../debugger/using-the-debuggerdisplay-attribute.md) bir nesne, özellik veya alanın hata ayıklayıcı değişken pencerelerinin nasıl görüntülendiğini denetler.

**Ne zaman:** Kodunuzda hata ayıklayıcı içindeki özellikleri programlama yoluyla [sabitlemek](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) istiyorsunuz.

**Neden:** Sabitleme özellikleri, nesne hata ayıklayıcı içindeki özellik listesinin en üstüne bu özelliği ayıklayana ekleyerek nesneleri özelliklerine göre hızlıca incelemenizi sağlar. 

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir tür, temsilci, özellik veya alana yerleştirin. 

2. **CTRL** tuşuna basın + **.** **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü tetiklemek ve **DebuggerDisplay özniteliği Ekle**' yi seçin.

    ![Karşılaştırma İşleçleri Oluştur](media/add-debugger-display-attribute.png)

3. DebuggerDisplay özniteliği, varsayılan ToString () değerini döndüren bir Auto yöntemiyle birlikte eklenir. 

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)