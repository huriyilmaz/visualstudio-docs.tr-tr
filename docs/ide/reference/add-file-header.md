---
title: Dosya üstbilgisi Ekle
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44cf9c34a69d665186a9f386e7ec34c5a59b8cdc
ms.sourcegitcommit: 8b1314ceab58e0d562cdbb1367fa738fdca7bf1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86285387"
---
# <a name="add-file-header"></a>Dosya üstbilgisi Ekle

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
