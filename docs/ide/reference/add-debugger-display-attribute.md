---
title: DebuggerDisplay özniteliği Ekle
description: Hata ayıklayıcı değişkeni penceresinin bir nesneyi, özelliği veya alanı nasıl görüntülediğini denetlemek için DebuggerDisplay özniteliğini nasıl ekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 5e72c2ddba9bfbca2c3fdaa43ae1f278009e3960
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028039"
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