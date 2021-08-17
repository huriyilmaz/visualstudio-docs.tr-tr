---
title: Metot imzasını değiştirme
description: Yöntemin parametrelerini ekleyin, kaldırın veya sıralamayı değiştirme. yöntemine sağ tıklayın, Hızlı Eylemler ve Yeniden Düzenleme'yi seçin ve İmzayı Değiştir'i seçin.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e759d3d255b9b5d87608736e825276a0e05a3aca622dbfe3d886c0b486cc1a73
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372705"
---
# <a name="change-a-method-signature-refactoring"></a>Yöntem imzası yeniden düzenlemesini değiştirme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir yöntemin parametrelerini kaldırmanız veya sıralamayı değiştirmenizi sağlar.

**Ne zaman:** Şu anda çeşitli konumlarda kullanılan bir yöntem parametresini taşımak veya kaldırmak istediğiniz.

**Neden:** Parametreleri el ile kaldırabilir ve yeniden sıralayabilirsiniz, ardından bu yönteme yapılan tüm çağrıları bulabilir ve bunları tek tek değiştirebilirsiniz, ancak bu hatalara neden olabilir.  Bu yeniden düzenleme aracı görevi otomatik olarak gerçekleştirecek.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini değiştirmek için yöntemin adının veya kullanımlarından birinin içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod C #](media/changesignature-highlight-cs.png)

   - VB:

       ![Vurgulanan kod Visual Basic](media/changesignature-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R tuşlarına** ve ardından **Ctrl+V tuşlarına basın.**  (Seçtiğiniz profile bağlı olarak klavye kısayolu farklı olabilir.)
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve **Yeniden Düzenleme menüsünü tetikler ve** Önizleme penceresi açılır penceresinde **İmzayı** Değiştir'i seçin.
   - **Fare**
      - Parametreleri **Kaldır > Düzenle'> Düzenle'yi seçin.**
      - Parametreleri **Yeniden Sırala > Düzenle'> Düzenle'yi seçin.**
      - Koda sağ tıklayın, Hızlı Eylemler **ve Yeniden** Düzenleme menüsünü seçin ve Önizleme **penceresi** açılır penceresinde İmzayı Değiştir'i seçin.

3. Açılan **İmzayı** Değiştir iletişim kutusunda, yöntem imzasını değiştirmek için sağ tarafındaki düğmeleri kullanabilirsiniz:

   ![İmzayı Değiştir iletişim kutusu](media/change-signature.png)

   | Düğme | Açıklama
   | ------ | ---
   | **Yukarı/Aşağı** | Seçilen parametreyi listede yukarı ve aşağı taşıma
   | **Ekle** | Listeye yeni bir parametre ekleme
   | **Kaldır** | Seçili parametreyi listeden kaldırma
   | **Geri yükleme** | Seçilen, çapraz parametreyi listeye geri yükleme

   > [!TIP]
   > Başvuru **değişikliklerini önizle** onay kutusunu [kullanarak işlemeden önce sonucun](../../ide/preview-changes.md) ne olacağını görebilirsiniz.

4. İmzayı **Değiştir** iletişim **kutusunda Ekle'yi** seçmek Parametre Ekle **iletişim kutusunu** açar. **Parametre Ekle** iletişim kutusu bir tür adı ve parametre adı eklemenize olanak sağlar. Parametreyi bir varsayılan değerle gerekli veya isteğe bağlı hale getirmeyi seçebilirsiniz. Daha sonra çağrı sitesine bir değer ekleyip bu değere yönelik adlandırılmış bir bağımsız değişken seçebilir veya bir TODO değişkeni tanıtabilirsiniz. Her hatayı ziyaret edip her çağrı sitesini bağımsız olarak kontrol edebilmeniz ve neyin geçirileceğine karar verebilmeniz için TODO değişkeni, kodunuza bir TODO ekler. İsteğe bağlı parametrelerde çağrı sitesini tamamen atlama seçeneğiniz vardır.

    ![Parametre Ekle iletişim kutusu - C #](media/add-parameter-dialog.png)

5. Parametre eklemeyi bitirdikten sonra değişikliklerin önizlemesini görmek **için Tamam'a** basın.

    ![İmzayı Değiştir iletişim kutusu](media/change-signature.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)