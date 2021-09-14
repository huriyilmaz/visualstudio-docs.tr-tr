---
title: Arabirim yeniden düzenlemesi Ayıkla
description: Bir sınıf, yapı veya arabirimden var olan üyeleri kullanarak bir arabirim oluşturmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725746"
---
# <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi Ayıkla

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf, yapı veya arabirimden var olan üyeleri kullanarak bir arabirim oluşturmanıza olanak sağlar.

**Ne zaman:** Başka sınıflar, yapılar veya arabirimler tarafından devralınabilir bir sınıf, yapı veya arabirimdeki üyelere sahipsiniz.

**Neden:** Arabirimler, nesne odaklı tasarımlar için harika yapılardır. çeşitli hayvanlar (köpek, kedi, kedi) için, hepsi yiyecek, drınk, uyku gibi ortak yöntemlere sahip olabilecek Imagine. Ihayvan gibi bir arabirim kullanmak, bu yöntemler için köpek, Cat ve Bird ortak bir "imzaya" sahip olmasını sağlar.

## <a name="extract-an-interface-refactoring"></a>Arabirim yeniden düzenlemesi Ayıkla

1. İmlecinizi sınıf adına yerleştirin.

   - C#:

       ![Vurgulanan kod-C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/extractinterface-highlight-vb.png)

2. Sonra, aşağıdaki eylemlerden birini yapın:

   - **Klavye**
      - **CTRL + R**, ardından **CTRL + ı** tuşlarına basın. (Klavye kısayolunuz, seçtiğiniz profile bağlı olarak farklı olabilir.)
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinden **Arabirimi Ayıkla** ' yı seçin.
   - **Fare**
      - **Arabirimi ayıkla > düzenle > yeniden Düzenle**' yi seçin.
      - Sınıfın adına sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **Arabirimi Ayıkla** ' yı seçin.

3. Açılan **Arabirimi Ayıkla** iletişim kutusunda, istenen bilgileri girin:

   ![Ayıklama Arabirimi](media/extractinterface-dialog-same-file.png)

   | Alan | Açıklama |
   | - | - |
   | **Yeni arabirim adı** | Oluşturulacak arabirimin adı. Ad varsayılan olarak I *ClassName* olarak, burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. |
   | **Yeni dosya adı** | Arabirimi içerecek oluşturulan dosyanın adı. Arabirim adında olduğu gibi, bu ad varsayılan olarak I *ClassName* olur; burada *ClassName* yukarıda seçtiğiniz sınıfın adıdır. Ayrıca **geçerli dosyaya ekleme** seçeneğini de belirleyebilirsiniz. |
   | **Arabirim oluşturmak için ortak üyeleri seçin** | Arabirime Ayıklanacak öğeler. İstediğiniz kadar istediğiniz kadar seçebilirsiniz. |

4. **Tamam ' ı** seçin.

   Arabirim, belirtilen ad dosyasında oluşturulur. Ayrıca, seçtiğiniz sınıf bu arabirimi uygular.

   - C#:

      ![Elde edilen sınıf-C #](media/extractinterface-class-cs.png)

      ![Sonuç arabirimi-C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Elde edilen sınıf-Visual Basic](media/extractinterface-class-vb.png)

      ![Sonuç arabirimi-Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.net geliştiricileri için İpuçları](../csharp-developer-productivity.md)
