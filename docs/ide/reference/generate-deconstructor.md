---
title: Yok etme hızlı eylemi oluşturma
description: Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanarak yeni bir yıkıcı için hemen yöntem saplama oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eb6ffb06436b36382925fb33ff4fbb35626e8a21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151658"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Visual Studio'de bir deconstructor oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

**Ne:** Yeni bir yıkıcı için yöntem saplamalarını hemen oluşturmana olanak sağlar.

**Ne zaman:** Tür türlerinizi otomatik olarak düzgün bir şekilde yok etmek istediğiniz.

**Neden:** Bir yıkıcıyı el ile yazabilirsiniz, ancak bu özellik doğru out parametreleriyle saplamayı sizin için üretir.

## <a name="generate-a-deconstructor"></a>Yıkıcı oluşturma

1. İstenen out parametreleri belirtilen yeni bir tür bildirebilirsiniz. Bildiriminiz ile eşleşen bir yok etme örneği bulunamaması bu bildirimde hataya neden olur.

   ![Yok etme hatası eksik](media/deconstruct.png)

2. Aşağıdaki adımlardan birini uygulayın:

   - **Klavye**
      - İmleç bildiriminize ek olarak Ctrl+ tuşlarını seçin. hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Metin :::image type="icon" source="media/screwdriver.png"::: imleci sınıftaki boş satırda zaten varsa sol kenar boşluğunda görünen simgeyi seçin.

      ![Yıkıcı kod düzeltmesi oluşturma](media/deconstruct-codefix.png)

3. **Deconstructor'ı oluşturmak için Generate method 'MyInternalClass.Deconstruct' (MyInternalClass.Deconstruct'** yöntemini oluştur) öğesini seçin.

   ![Sonuçta elde edilen yok etme kodu](media/deconstruct-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)