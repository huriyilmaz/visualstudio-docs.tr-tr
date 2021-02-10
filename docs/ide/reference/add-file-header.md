---
title: Dosya üst bilgisi ekleme
description: Varolan dosyalara, projelere ve çözümlere dosya üstbilgileri eklemek için bir EditorConfig dosyası kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2b177092b04d5042f62dfd0b34d2bfbf4f1f0228
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933875"
---
# <a name="add-file-header"></a>Dosya üst bilgisi ekleme

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir [Editorconfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)kullanarak var olan dosyalara, projelere ve çözümlere dosya üstbilgileri ekleyin.

**Ne zaman:** Dosyalara, projelere ve çözümlere kolayca bir dosya üstbilgisi eklemek istiyorsunuz.

**Neden:** Takımınız, telif hakkı amaçları için bir dosya üst bilgisi eklemeniz gerekir. 

## <a name="how-to"></a>Nasıl yapılır

1. Henüz bir tane yoksa bir projeye veya çözüme bir [Editorconfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) ekleyin.

2. Aşağıdaki kuralı EditorConfig dosyanıza ekleyin: *file_header_template*.

3. Kuralın değerini, uygulamak istediğiniz üst bilgi metnine eşit olacak şekilde ayarlayın. `{fileName}`Dosya adı için bir yer tutucu olarak kullanabilirsiniz.

    ![File_header_template değerini gösteren EditorConfig dosyasının ekran görüntüsü.](media/add-file-header-rule.png)

    > [!NOTE]
    > Bir EditorConfig içinde açık multilines olamaz ve yeni satırlar eklemek için UNIX yeni satır karakterini kullanmanız gerekir.

4. Giriş işaretini herhangi bir C# veya Visual Basic dosyasının ilk satırına yerleştirin.

5. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

6. **Dosya başlığı Ekle**' yi seçin. 

    ![Dosya üst bilgisi ekle seçeneğinin ekran görüntüsü.](media/add-file-header.png)

7. Dosya üstbilgisini bir proje veya çözüme uygulamak için, **içindeki tüm oluşumları çözümle:** seçeneğini altında **Proje** veya **çözüm** ' ı seçin.

8. Değişiklikleri gözden geçirebileceğiniz **tüm oluşumları düzeltir** iletişim kutusu açılır.

    ![Tüm oluşumları çözme iletişim kutusu](media/file-header-preview-changes.png)

8. Değişiklikleri uygulamak için **Uygula** ' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)