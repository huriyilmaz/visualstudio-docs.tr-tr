---
title: Dosya üst bilgisi ekleme
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 779092e277ac5b6eed3afcaceaf55b26ee2759dd
ms.sourcegitcommit: 025816f8e388b29e58761d304b0fda755ac5a613
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374175"
---
# <a name="add-file-header"></a>Dosya üst bilgisi ekleme

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir [Editorconfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)kullanarak var olan dosyalara, projelere ve çözümlere dosya üstbilgileri ekleyin.

**Ne zaman:** Dosyalara, projelere ve çözümlere kolayca bir dosya üstbilgisi eklemek istiyorsunuz.

**Neden:** Takımınız, telif hakkı amaçları için bir dosya üst bilgisi eklemeniz gerekir. 

## <a name="how-to"></a>Nasıl yapılır

1. Henüz bir tane yoksa bir projeye veya çözüme bir [Editorconfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) ekleyin.

2. Aşağıdaki kuralı EditorConfig dosyanıza ekleyin: *file_header_template*.

3. Kuralın değerini, uygulamak istediğiniz üst bilgi metnine eşit olacak şekilde ayarlayın.

    ![EditorConfig dosyası üst bilgi kuralı](media/add-file-header-rule.png)

> [!NOTE]
> Bir EditorConfig içinde açık multilines olamaz ve yeni satırlar eklemek için UNIX yeni satır karakterini kullanmanız gerekir.

4. Giriş işaretini herhangi bir C# veya Visual Basic dosyasının ilk satırına yerleştirin.

5. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

6. **Dosya başlığı Ekle**' yi seçin. 

    ![EditorConfig dosyası üst bilgi kuralı](media/add-file-header.png)

7. Dosya üstbilgisini bir proje veya çözüme uygulamak için, **içindeki tüm oluşumları çözümle:** seçeneğini altında **Proje** veya **çözüm** ' ı seçin.

8. Değişiklikleri gözden geçirebileceğiniz **tüm oluşumları düzeltir** iletişim kutusu açılır.

    ![Tüm oluşumları çözme iletişim kutusu](media/file-header-preview-changes.png)

8. Değişiklikleri uygulamak için **Uygula** ' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
