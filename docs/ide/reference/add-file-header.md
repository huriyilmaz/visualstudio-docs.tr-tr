---
title: Dosya üst bilgisi ekleme
description: EditorConfig dosyasını kullanarak mevcut dosyalara, projelere ve çözümlere dosya üst bilgileri ekleme hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: f902d90de1260b1dde17bb4570a4841bd73bbe42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094353"
---
# <a name="add-file-header"></a>Dosya üst bilgisi ekleme

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** EditorConfig kullanarak mevcut dosyalara, projelere ve çözümlere dosya üst [bilgileri ekleyin.](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

**Ne zaman:** Dosyalara, projelere ve çözümlere kolayca bir dosya üst bilgisi eklemek istediğiniz.

**Neden:** Takımınız, telif hakkı amacıyla bir dosya üst bilgisi dahil etmek zorunda. 

## <a name="how-to"></a>Nasıl yapılır

1. Henüz bir projeniz veya çözümünüz yoksa [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) ekleyin.

2. EditorConfig dosyanıza şu kuralı ekleyin: *file_header_template.*

3. Kuralın değerini, uygulanması istediğiniz üst bilgi metnine eşit olacak şekilde ayarlayın. Dosya adı `{fileName}` için yer tutucu olarak kullanabilirsiniz.

    ![File_header_template değerini gösteren EditorConfig dosyasının ekran görüntüsü.](media/add-file-header-rule.png)

    > [!NOTE]
    > EditorConfig içinde açık çoklu çizgileriniz olamaz ve yeni satırlar eklemek için Unix yeni satır karakterinin kullanımı gerekir.

4. Herhangi bir C# veya dosyanın ilk satırına Visual Basic.

5. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

6. Dosya **üst bilgisi ekle'yi seçin.** 

    ![Dosya üst bilgisi ekle seçeneğinin ekran görüntüsü.](media/add-file-header.png)

7. Dosya üst bilgilerini bir projenin veya çözümün tamamına  uygulamak için Şu **Project** tüm oluşumları düzelt: seçeneğinin altında Çözüm veya **Çözüm'e** tıklayın.

8. Tüm **oluşumları düzelt** iletişim kutusu açılır ve burada değişikliklerin önizlemesini görebilirsiniz.

    ![Tüm oluşumları düzelt iletişim kutusu](media/file-header-preview-changes.png)

8. Değişiklikleri **uygulamak** için Uygula'ya seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)