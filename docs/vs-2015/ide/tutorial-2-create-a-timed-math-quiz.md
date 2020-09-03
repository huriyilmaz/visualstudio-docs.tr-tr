---
title: 'Öğretici 2: zamanlı matematik testi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b91e5f864bc15f1fbcab9400d0cd3a4a2e8224a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299869"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Eğitmen 2: Zamanlı Matematik Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, bir sınavın belirli bir süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test oluşturacaksınız. Aşağıdakileri nasıl yapacağınızı öğrenirsiniz:

- Sınıfını kullanarak rastgele sayılar üretin `Random` .

- Bir **Zamanlayıcı** denetimi kullanarak olayları belirli bir zamanda gerçekleşecek şekilde tetikleyin.

- Deyimlerini kullanarak program akışını denetleme `if else` .

- Kodda temel aritmetik işlemler gerçekleştirin.

  Bitirdiğinizde, test, farklı sayılar dışında aşağıdaki resme benzer şekilde görünür.

  ![Dört problemle matematik sınavından](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Bu öğreticide oluşturduğunuz test

> [!NOTE]
> Bu öğreticide hem Visual C# hem de Visual Basic ele alınmaktadır, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanırsınız.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Projeyi oluşturarak, özellikleri değiştirerek ve denetimler ekleyerek başlayın `Label` .|
|[2. Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Ek bir sorun oluşturun ve `Random` rastgele sayılar oluşturmak için sınıfını kullanın.|
|[3. Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)|Sınavın zaman aşımına uğraabilmesi için bir geri sayım Zamanlayıcısı ekleyin.|
|[4. Adım: CheckTheAnswer () metodunu ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınavın sorun için doğru bir yanıt girmediğini denetlemek için bir yöntem ekleyin.|
|[5. Adım: NumericUpDown denetimleri için giriş olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Sınavını daha kolay hale getirmek için olay işleyicileri ekleyin.|
|[6. Adım: çıkarma sorunu ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rastgele sayılar üreten, Zamanlayıcı kullanan ve doğru yanıtları denetleyen bir çıkarma sorunu ekleyin.|
|[7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rastgele sayılar üreten çarpma ve bölme sorunları ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[8. Adım: testi özelleştirme](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|
