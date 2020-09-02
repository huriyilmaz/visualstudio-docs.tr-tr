---
title: Metot imzasını değiştirme
description: Metodun parametrelerini ekleyin, kaldırın veya sırasını değiştirin. Yöntemine sağ tıklayın, hızlı eylemler ve yeniden düzenlemeler ' ı seçin ve Imzayı Değiştir ' i seçin.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d91406b65950515afb3659c0d5918841465b2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86869574"
---
# <a name="change-a-method-signature-refactoring"></a>Yöntem imzasını yeniden düzenlemeyi değiştirme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir yöntemin parametrelerinin sırasını kaldırmanıza veya değiştirmenize olanak sağlar.

**Ne zaman:** Şu anda çeşitli konumlarda kullanılmakta olan bir yöntem parametresini taşımak veya kaldırmak istiyorsunuz.

**Neden:** Parametreleri el ile kaldırıp yeniden sıralayın ve sonra bu yönteme yapılan tüm çağrıları bulabilir ve bunları tek tek değiştirebilir ancak bu hatalara yol açabilir.  Bu yeniden düzenleme aracı görevi otomatik olarak gerçekleştirir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini, değiştirilecek metodun adının içine veya kullanımlarından birine göre vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanmış kod C #](media/changesignature-highlight-cs.png)

   - VB

       ![Vurgulanan kod Visual Basic](media/changesignature-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL + R**, ardından **CTRL + V**tuşlarına basın.  (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
      - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **imzayı Değiştir** ' i seçmek için.
   - **Fare**
      - **Parametreleri kaldırmak > düzenle > yeniden Düzenle**' yi seçin.
      - **Düzenle > yeniden düzenleme > parametreleri yeniden**düzenleyin ' i seçin.
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinde **imzayı Değiştir** ' i seçin.

3. Açılan **Imza Değiştir** iletişim kutusunda, yöntem imzasını değiştirmek için sağ taraftaki düğmeleri kullanabilirsiniz:

   ![Imza değiştirme iletişim kutusu](media/change-signature.png)

   | Düğme | Description
   | ------ | ---
   | **Yukarı/aşağı** | Seçili parametreyi listede yukarı ve aşağı taşı
   | **Ekle** | Listeye yeni bir parametre Ekle
   | **Kaldır** | Seçili parametreyi listeden kaldır
   | **Geri yükleme** | Seçilen, çapraz çıkış parametresini listeye geri yükleme

   > [!TIP]
   > Sonucun kendisine işlemeden önce [ne olacağını görmek](../../ide/preview-changes.md) için **başvuru değişikliklerini Önizle** onay kutusunu kullanın.

4. **Imza Değiştir** Iletişim kutusunda **Ekle** ' nin seçilmesi **parametre Ekle** iletişim kutusunu açar. **Parametre Ekle** iletişim kutusu bir tür adı ve parametre adı eklemenize olanak sağlar. Parametreyi bir varsayılan değerle gerekli veya isteğe bağlı hale getirmeyi seçebilirsiniz. Daha sonra çağrı sitesine bir değer ekleyip bu değere yönelik adlandırılmış bir bağımsız değişken seçebilir veya bir TODO değişkeni tanıtabilirsiniz. Her hatayı ziyaret edip her çağrı sitesini bağımsız olarak kontrol edebilmeniz ve neyin geçirileceğine karar verebilmeniz için TODO değişkeni, kodunuza bir TODO ekler. İsteğe bağlı parametrelerde çağrı sitesini tamamen atlama seçeneğiniz vardır.

    ![Parametre Ekle iletişim kutusu-C #](media/add-parameter-dialog.png)

5. Bir parametre ekleme işiniz bittiğinde değişiklikleri önizlemek için **Tamam** ' a basın.

    ![Imza değiştirme iletişim kutusu](media/change-signature.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)