---
title: Arabirim yeniden düzenlemesi ayıklama
description: Bir sınıftan, yapıdan veya arabirimden mevcut üyeleri kullanarak arabirim oluşturmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 980a6634bf1be60e36f267bf54d1b03f227281dc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094106"
---
# <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıftan, yapıdan veya arabirimden mevcut üyeleri kullanarak bir arabirim oluşturmanıza olanak sağlar.

**Ne zaman:** Diğer sınıflar, yapılar veya arabirimler tarafından devralınabilir bir sınıf, yapı veya arabirimde üyelerine sahipsiniz.

**Neden:** Arabirimler, nesne odaklı tasarımlara yönelik harika yapılardır. Imagine hayvanlar (Köpek, Kedi, Kuş) için sınıfların olması gerekir. Bunların hepsi yemek, içecek, uyku gibi ortak yöntemlere sahip olabilir. IAnimal gibi bir arabirim kullanmak Köpek, Kedi ve Bird'in bu yöntemler için ortak bir "imzaya" sahip olmasına olanak sağlar.

## <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi ayıklama

1. İmlecinizi sınıf adına yerleştirin.

   - C#:

       ![Vurgulanan kod - C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/extractinterface-highlight-vb.png)

2. Ardından, aşağıdaki eylemlerden birini yapın:

   - **Klavye**
      - **Ctrl+R tuşlarına** ve ardından **Ctrl+I tuşlarına basın.** (Klavye kısayolu, seçtiğiniz profile göre farklı olabilir.)
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve **Yeniden Düzenleme menüsünü tetiklemek için** Önizleme penceresi açılır penceresinde **Arabirimi** Ayıkla'ya tıklayın.
   - **Fare**
      - Arabirimi **Ayıkla > Düzenle'> Düzenle'yi seçin.**
      - Sınıfın adına sağ tıklayın, Hızlı Eylemler ve **Yeniden** Düzenleme menüsünü  seçin ve Önizleme penceresi açılır penceresinde Arabirimi Ayıkla'yı seçin.

3. Açılan **Arabirimi Ayıkla** iletişim kutusunda sorulan bilgileri girin:

   ![Ayıklama Arabirimi](media/extractinterface-dialog-same-file.png)

   | Alan | Açıklama |
   | - | - |
   | **Yeni arabirim adı** | Oluşturulacak arabirimin adı. Ad varsayılan olarak I *ClassName olur;* burada *ClassName,* yukarıda seçtiğiniz sınıfın adıdır. |
   | **Yeni dosya adı** | Arabirimini içeren oluşturulan dosyanın adı. Arabirim adı gibi, bu ad varsayılan olarak I *ClassName* olur; burada *ClassName,* yukarıda seçtiğiniz sınıfın adıdır. Geçerli dosyaya ekle seçeneğini **de belirleyin.** |
   | **Arabirim oluşturmak için genel üyeleri seçme** | Arabirime ayıklanan öğeler. İstediğiniz sayıda seçim de ve ardından bunu da seçerek. |

4. **Tamam'ı seçin.**

   Arabirim, belirtilen adın dosyasında oluşturulur. Ayrıca, seçtiğiniz sınıf bu arabirimini uygulayan.

   - C#:

      ![Sonuçta Elde Edilen Sınıf - C #](media/extractinterface-class-cs.png)

      ![Sonuçta Elde Edilen Arabirim - C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Sonuç Sınıfı - Visual Basic](media/extractinterface-class-vb.png)

      ![Sonuçta Elde Edilen Arabirim - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri İpuçları için geliştirmeler](../csharp-developer-productivity.md)
