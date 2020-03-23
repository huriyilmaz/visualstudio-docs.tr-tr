---
title: Arabirim refactoring ayıklama
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595676"
---
# <a name="extract-an-interface-refactoring"></a>Arabirim refactoring ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıftan, yapıdan veya arabirimden varolan üyeleri kullanarak bir arabirim oluşturmanıza olanak tanır.

**Ne zaman:** Diğer sınıflar, structs veya arabirimler tarafından devralınabilir bir sınıf, yapı veya arabirim üyeleri var.

**Neden:** Arayüzler nesne yönelimli tasarımlar için harika yapılardır. Eat, Drink, Sleep gibi ortak yöntemleri olan çeşitli hayvanlar (Köpek, Kedi, Kuş) için sınıflara sahip olduğunuzu düşünün. IAnimal gibi bir arayüz kullanarak Köpek, Kedi ve Kuş bu yöntemler için ortak bir "imza" olması için izin verir.

## <a name="extract-an-interface-refactoring"></a>Arabirim refactoring ayıklama

1. İmlecinizi sınıf adına yerleştirin.

   - C#:

       ![Vurgulanan kod - C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/extractinterface-highlight-vb.png)

2. Ardından, aşağıdaki eylemlerden birini yapın:

   - **Klavye**
      - **Ctrl+R**tuşuna basın, sonra **Ctrl+I**tuşuna basın. (Klavyekısayol'unuzun kısaltması seçtiğiniz profile bağlı olarak farklı olabilir.)
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek ve Önizleme penceresinden **Arabirimi Ayıkla'yı** seçin.
   - **Fare**
      - Refactor **> Ayıkla arayüzünü düzenleme'> yi**seçin.
      - Sınıfın adını sağ tıklatın, Hızlı **Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **Arabirimi Ayıkla'yı** seçin.

3. Açılan **Extract Arabirimi** iletişim kutusuna sorulan bilgileri girin:

   ![Ayıklama Arabirimi](media/extractinterface-dialog-same-file.png)

   | Alan | Açıklama |
   | - | - |
   | **Yeni arayüz adı** | Oluşturulacak arabirimin adı. Ad, *ClassName'nin* yukarıda seçtiğiniz sınıfın adı olduğu I*ClassName'de*varsayılan olarak yer alır. |
   | **Yeni dosya adı** | Arabirimi içerecek şekilde oluşturulan dosyanın adı. Arabirim adında olduğu gibi, bu ad varsayılan olarak, *ClassName'nin* yukarıda seçtiğiniz sınıfın adı olduğu I*ClassName'ye*göre varsayılan olarak verilir. **Geçerli dosyaya ekle**seçeneğini de seçebilirsiniz. |
   | **Arayüz oluşturmak için ortak üyeleri seçin** | Arabiriminiçine çıkarılacak öğeler. İstediğiniz kadar seçebilirsiniz. |

4. **Tamam'ı**seçin.

   Arabirim belirtilen adın dosyasında oluşturulur. Ayrıca, seçtiğiniz sınıf bu arabirimi uygular.

   - C#:

      ![Elde Eden Sınıf - C #](media/extractinterface-class-cs.png)

      ![Ortaya Çıkan Arayüz - C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Elde Eden Sınıf - Visual Basic](media/extractinterface-class-vb.png)

      ![Ortaya Çıkan Arayüz - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
