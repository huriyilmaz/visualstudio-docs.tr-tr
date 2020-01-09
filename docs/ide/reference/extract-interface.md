---
title: Bir arabirimi yeniden düzenleme ayıklayın
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5055f50d07cf9362c9be1bdc8135e31240a7cc66
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595676"
---
# <a name="extract-an-interface-refactoring"></a>Bir arabirimi yeniden düzenleme ayıklayın

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf, yapı veya arabirimden var olan üyeleri kullanarak bir arabirim oluşturmanıza olanak sağlar.

**Ne zaman:** Başka sınıflar, yapılar veya arabirimler tarafından devralınabilir bir sınıf, yapı veya arabirimdeki üyelere sahipsiniz.

**Neden:** harika yapılar için nesne yönelimli tasarım arabirimdir. Sınıflar için tüm Eat, içecek, uyku gibi yaygın yöntemleri olabilir çeşitli hayvanlar (Dog, Kedi, Bird) sahip olduğunuzu düşünelim. IAnimal gibi bir arabirim kullanarak köpek Cat ve Bird ortak bir "SIGNATURE" Bu yöntemlere ait olmasını çalıştırmasına olanak tanır.

## <a name="extract-an-interface-refactoring"></a>Bir arabirimi yeniden düzenleme ayıklayın

1. İmlecinizi sınıf adına yerleştirin.

   - C#:

       ![Vurgulanan kodu:C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu - Visual Basic](media/extractinterface-highlight-vb.png)

2. Sonra, aşağıdaki eylemlerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl + R**, ardından **Ctrl + ı**. (Klavye kısayolunuz, seçtiğiniz profile bağlı olarak farklı olabilir.)
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **Arabirimi Ayıkla** gelen önizleme penceresi açılır.
   - **Fare**
      - Seçin **Düzenle > yeniden düzenleyin > Arabirimi Ayıkla**.
      - Select sınıf adına sağ tıklayın **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **Arabirimi Ayıkla** gelen önizleme penceresi açılır.

3. İçinde **Arabirimi Ayıkla** , açılan iletişim kutusunda sorulan bilgileri girin:

   ![Ayıklama Arabirimi](media/extractinterface-dialog-same-file.png)

   | Alan | Açıklama |
   | - | - |
   | **Yeni arabirimin adı** | Oluşturulacak arabirimin adı. Ad varsayılan olarak I*ClassName*olarak, burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. |
   | **Yeni dosya adı** | Arabirimi içerecek oluşturulan dosyanın adı. Arabirim adında olduğu gibi, bu ad varsayılan olarak I*ClassName*olur; burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. Ayrıca **geçerli dosyaya ekleme**seçeneğini de belirleyebilirsiniz. |
   | **Form arabirimi için genel üyeleri seçin** | Ayıklama arabirimi öğelerdir. İstediğiniz kadar çok seçebilirsiniz. |

4. **Tamam**’ı seçin.

   Belirtilen adı dosyasında arabirimi oluşturulur. Buna ek olarak, seçtiğiniz sınıfı bu arabirimi uygular.

   - C#:

      ![Elde edilen sınıf-C#](media/extractinterface-class-cs.png)

      ![Sonuç arabirimi-C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Elde edilen sınıf-Visual Basic](media/extractinterface-class-vb.png)

      ![Sonuç arabirimi-Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için İpuçları](../csharp-developer-productivity.md)
