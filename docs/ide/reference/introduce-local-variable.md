---
title: Bir yerel değişken ekleme
description: Varolan bir ifadeyi değiştirmek için yerel bir değişken oluşturun. İfadeyi seçin, sağ tıklayın ve hızlı eylemler ve yeniden düzenlemeler menüsünü seçin, ' expression ' ' ın (tüm oluşumlar) için yerel Ekle ' yi seçin.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568821"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio'da bir yerel değişken ekleme

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** hemen var olan bir ifade değiştirmek için bir yerel değişken oluşturmanıza olanak tanır.

**Ne zaman:** yerel bir değişkende olsaydı, kolayca daha sonra yeniden kullanılabilen kodlarla koda sahip.

**Neden:** kopyalayın ve sonra işlemi gerçekleştirmek, sonucu yerel bir değişkende depolar ve yerel bir değişken boyunca kullanmanız daha iyi ancak kodu çeşitli konumlarda kullanmak için birden çok kez yapıştırın.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Yeni bir yerel değişkene atamak istediğiniz ifade vurgulayın.

   - C#:

       ![Vurgulanmış kodu C#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu VB](media/local-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - &nbsp; ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda görüntülenen simge, metin imleç zaten vurgulanan ifade ile satırda varsa görüntülenir.

   ![Yerel Önizleme Ekle](media/local-preview-cs.png)

3. Açılan menüden **' expression ' için yerel (tüm oluşumlar) Ekle '** yi seçin.

   > [!TIP]
   > Kullanım **değişiklik önizlemesi** Önizleme pencerenin alt kısmındaki bağlantı [tüm değişiklikleri görmek için](../../ide/preview-changes.md) , oluşturulacak, seçim yapmadan önce.

   Yerel değişken, kullanımdan çıkarılan türü ile oluşturulur. Yeni yerel değişkeni, yeni bir ad verin.

   - C#:

       ![C# arabirimi sonucu uygulayın](media/local-result-cs.png)

   - Visual Basic:

       ![Uygulama arabirimi sonucu VB](media/local-result-vb.png)

   > [!NOTE]
   > Kullanabileceğiniz **.. .all oluşumlarını...**  menü seçeneğini seçili ifadesi, yalnızca özellikle vurgulanmış bir her örneğini değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)
