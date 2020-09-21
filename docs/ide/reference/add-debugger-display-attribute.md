---
title: DebuggerDisplay özniteliği Ekle
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: db49bfd1672866a755cce6780527520da2cad420
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810395"
---
# <a name="add-debuggerdisplay-attribute"></a>DebuggerDisplay özniteliği Ekle

Bu kod üretimi için geçerlidir:

- C#

**Ne:** [DebuggerDisplay özniteliği](../../debugger/using-the-debuggerdisplay-attribute.md) bir nesne, özellik veya alanın hata ayıklayıcı değişken pencerelerinin nasıl görüntülendiğini denetler.

**Ne zaman:** Kodunuzda hata ayıklayıcı içindeki özellikleri programlama yoluyla [sabitlemek](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) istiyorsunuz.

**Neden:** Sabitleme özellikleri, nesne hata ayıklayıcı içindeki özellik listesinin en üstüne bu özelliği ayıklayana ekleyerek nesneleri özelliklerine göre hızlıca incelemenizi sağlar. 

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir tür, temsilci, özellik veya alana yerleştirin. 

2. **CTRL**tuşuna basın + **.** **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü tetiklemek ve **DebuggerDisplay özniteliği Ekle**' yi seçin.

    ![Karşılaştırma İşleçleri Oluştur](media/add-debugger-display-attribute.png)

3. DebuggerDisplay özniteliği, varsayılan ToString () değerini döndüren bir Auto yöntemiyle birlikte eklenir. 

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)