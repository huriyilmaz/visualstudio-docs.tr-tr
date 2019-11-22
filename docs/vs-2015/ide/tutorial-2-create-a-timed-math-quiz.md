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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299869"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Eğitmen 2: Zamanlı Matematik Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, bir sınavın belirli bir süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test oluşturacaksınız. Aşağıdakilerin nasıl yapıldığını öğreneceksiniz:

- `Random` sınıfını kullanarak rastgele sayılar üretin.

- Bir **Zamanlayıcı** denetimi kullanarak olayları belirli bir zamanda gerçekleşecek şekilde tetikleyin.

- `if else` deyimlerini kullanarak program akışını denetleme.

- Kodda temel aritmetik işlemler gerçekleştirin.

  Bitirdiğinizde, test, farklı sayılar dışında aşağıdaki resme benzer şekilde görünür.

  ![Dört problemle matematik sınavından](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Bu öğreticide oluşturduğunuz test

> [!NOTE]
> Bu öğreticide hem görsel C# hem de Visual Basic ele alınmaktadır, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanırsınız.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje Oluşturma ve Formunuza Etiketler Ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Projeyi oluşturarak, özellikleri değiştirerek ve `Label` denetimleri ekleyerek başlayın.|
|[2. Adım: Rasgele bir Toplama Problemi Oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Ek bir sorun oluşturun ve rastgele sayılar oluşturmak için `Random` sınıfını kullanın.|
|[3. Adım: Geri Sayım Zamanlayıcısı Ekleme](../ide/step-3-add-a-countdown-timer.md)|Sınavın zaman aşımına uğraabilmesi için bir geri sayım Zamanlayıcısı ekleyin.|
|[4. Adım: CheckTheAnswer() Yöntemi Ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınavın sorun için doğru bir yanıt girmediğini denetlemek için bir yöntem ekleyin.|
|[5. Adım: NumericUpDown Denetimleri için Giriş Olay İşleyicileri Ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Sınavını daha kolay hale getirmek için olay işleyicileri ekleyin.|
|[6. Adım: Çıkarma Problemi Ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rastgele sayılar üreten, Zamanlayıcı kullanan ve doğru yanıtları denetleyen bir çıkarma sorunu ekleyin.|
|[7. Adım: Çarpma ve Bölme Problemleri Ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rastgele sayılar üreten çarpma ve bölme sorunları ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[8. Adım: Testi Özelleştirme](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|
