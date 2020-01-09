---
title: 'Öğretici 2: süreli bir matematik testi oluşturma'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 884047237652f6b69bd437b5faf47d820903b824
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588674"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Öğretici 2: süreli bir matematik testi oluşturma

Bu öğreticide, bir sınavın belirli bir süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test oluşturacaksınız.

> [!NOTE]
> Bu öğretici hem hem C# de Visual Basic, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanırsınız.

Bu öğretici aşağıdaki görevlerde size kılavuzluk eder:

- <xref:System.Random> sınıfını kullanarak rastgele sayılar üretin.

- <xref:System.Windows.Forms.Timer> denetimi kullanarak olayları belirli bir zamanda gerçekleşecek şekilde tetikleyin.

- `if else` deyimlerini kullanarak program akışını denetleme.

- Kodda temel aritmetik işlemler gerçekleştirin.

Bitirdiğinizde, test, farklı sayılar dışında aşağıdaki ekran görüntüsüne benzer şekilde görünür:

![Dört problemle matematik sınavından](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Projeyi oluşturarak, özellikleri değiştirerek ve `Label` denetimleri ekleyerek başlayın.|
|[2. Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Ek bir sorun oluşturun ve rastgele sayılar oluşturmak için `Random` sınıfını kullanın.|
|[3. Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)|Sınavın zaman aşımına uğraabilmesi için bir geri sayım Zamanlayıcısı ekleyin.|
|[4. Adım: CheckTheAnswer () metodunu ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınavın sorun için doğru bir yanıt girmediğini denetlemek için bir yöntem ekleyin.|
|[5. Adım: NumericUpDown denetimleri için giriş olay işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Sınavını daha kolay hale getirmek için olay işleyicileri ekleyin.|
|[6. Adım: çıkarma sorunu ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rastgele sayılar üreten, Zamanlayıcı kullanan ve doğru yanıtları denetleyen bir çıkarma sorunu ekleyin.|
|[7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rastgele sayılar üreten çarpma ve bölme sorunları ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[8. Adım: testi özelleştirme](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|

Ayrıca harika, ücretsiz video öğrenimi kaynakları da mevcuttur. İçinde C#programlama hakkında daha fazla bilgi edinmek için bkz [ C# . temel bilgiler: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için, 1. **[Adım: proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** ile başlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticiler](/visualstudio/get-started/csharp/)
* [Visual Basic öğreticileri](/visualstudio/get-started/visual-basic/)
* [C++izleyin](/cpp/get-started/tutorial-console-cpp)
