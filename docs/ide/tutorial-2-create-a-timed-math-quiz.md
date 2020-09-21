---
title: 'Öğretici 2: süreli bir matematik testi oluşturma'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 738d32186a0bb0f1d4655f9afea3d236bf53ad4c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810854"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Öğretici 2: süreli bir matematik testi oluşturma

Bu öğreticide, bir sınavın belirli bir süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test oluşturacaksınız.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic yanı sıra, kullanmakta olduğunuz programlama diline özgü bilgilere de odaklanırsınız.

Bu öğretici aşağıdaki görevlerde size kılavuzluk eder:

- Sınıfını kullanarak rastgele sayılar üretin <xref:System.Random> .

- Olayları bir denetim kullanarak belirli bir zamanda gerçekleşecek şekilde tetikleyin <xref:System.Windows.Forms.Timer> .

- Deyimlerini kullanarak program akışını denetleme `if else` .

- Kodda temel aritmetik işlemler gerçekleştirin.

Bitirdiğinizde, test, farklı sayılar dışında aşağıdaki ekran görüntüsüne benzer şekilde görünür:

![Dört problemle matematik sınavından](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Projeyi oluşturarak, özellikleri değiştirerek ve denetimler ekleyerek başlayın `Label` .|
|[2. Adım: Rastgele bir toplama problemi oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Ek bir sorun oluşturun ve `Random` rastgele sayılar oluşturmak için sınıfını kullanın.|
|[3. Adım: Geri sayım zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)|Sınavın zaman aşımına uğraabilmesi için bir geri sayım Zamanlayıcısı ekleyin.|
|[4. Adım: CheckTheAnswer() yöntemi ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınavın sorun için doğru bir yanıt girmediğini denetlemek için bir yöntem ekleyin.|
|[5. Adım: NumericUpDown denetimleri için Giriş olay işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Sınavını daha kolay hale getirmek için olay işleyicileri ekleyin.|
|[6. Adım: Çıkarma problemi ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rastgele sayılar üreten, Zamanlayıcı kullanan ve doğru yanıtları denetleyen bir çıkarma sorunu ekleyin.|
|[7. Adım: Çarpma ve bölme problemleri ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rastgele sayılar üreten çarpma ve bölme sorunları ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[8. Adım: Testi özelleştirme](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|

Ayrıca harika, ücretsiz video öğrenimi kaynakları da mevcuttur. C# dilinde programlama hakkında daha fazla bilgi edinmek için bkz. [C# temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için, 1. **[Adım: proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** ile başlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)