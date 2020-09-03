---
title: Kodlanmış UI testleri için en iyi uygulamalar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2dffebeaa0349c149e319d20794f8b065baa5647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660683"
---
# <a name="best-practices-for-coded-ui-tests"></a>Kodlanmış UI Testleri için En İyi Yöntemler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, kodlanmış UI testleri geliştirirken izlenecek en iyi uygulamalar açıklanmaktadır.

 **Gereksinimler**

- Visual Studio Enterprise

## <a name="best-practices"></a>En İyi Uygulamalar
 Esnek kodlanmış bir UI testi oluşturmak için aşağıdaki yönergeleri kullanın.

- Mümkün olduğunda **KODLANMıŞ UI test oluşturucusunu** kullanın.

- `UIMap.designer.cs`Dosyayı doğrudan değiştirmeyin. Bunu yaparsanız dosyadaki değişikliklerin üzerine yazılır.

- Testinizi kayıtlı yöntemlerin bir dizisi olarak oluşturun. Bir yöntemi kaydetme hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

- Her kaydedilen yöntemin tek bir sayfa, form veya iletişim kutusu üzerinde işlem yapması gerekir. Her yeni sayfa, form veya iletişim kutusu için yeni bir test yöntemi oluşturun.

- Bir yöntem oluşturduğunuzda, varsayılan ad yerine anlamlı bir yöntem adı kullanın. Anlamlı bir ad yöntemin amacını belirlemenize yardımcı olur.

- Mümkün olduğunda, her bir kaydedilen yöntemi 10 ' dan az eylemden sınırlayın. Bu modüler yaklaşım, UI değişirse bir yöntemin değiştirilmesini kolaylaştırır.

- Otomatik olarak dosyaya bir onaylama yöntemi ekleyen **KODLANMıŞ UI test oluşturucusunu**kullanarak her bir onaylama işlemi oluşturun `UIMap.Designer.cs` .

- Kullanıcı arabirimi (UI) değişirse, test yöntemlerini veya onaylama yöntemlerini yeniden kaydedin veya var olan bir test yönteminin etkilenen bölümlerini yeniden kaydedin.

- Test edilen uygulamanızdaki her bir modül için ayrı bir [UIMap](/previous-versions/dd580454(v=vs.140)) dosyası oluşturun. Daha fazla bilgi için bkz. [birden çok UI haritası Ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md).

- Test edilen uygulamada, UI denetimlerini oluştururken anlamlı adlar kullanın. Bu, otomatik olarak oluşturulan denetim adlarına daha fazla anlam ve kullanılabilirlik sağlar.

- API ile kodlamaya göre onay oluşturuyorsanız, dosyadaki [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının bölümünde her onaylama için bir yöntem oluşturun `UIMap.cs` . Onaylama işlemi yürütmek için test yönteinizden bu yöntemi çağırın.

- Doğrudan API ile `UIMap.Designer.cs` kodladıysanız kodunuzdaki dosyada oluşturulan sınıflarda bulunan özellikleri ve yöntemleri kullanabilirsiniz. Bu sınıflar işinizi daha kolay, daha güvenilir hale getirir ve daha üretken olmanıza yardımcı olur.

  Kodlanmış UI testleri Kullanıcı arabirimindeki birçok değişikliğe otomatik olarak uyum sağlar. Örneğin, bir kullanıcı arabirimi öğesi konum veya renge değiştiyse, çoğu zaman kodlanmış UI testi doğru öğeyi bulmaya devam eder.

  Bir test çalıştırması sırasında, Kullanıcı arabirimi denetimleri, dosyadaki **KODLANMıŞ UI Test Oluşturucusu** tarafından oluşturulan tanımlarda her bir denetim sınıfına uygulanan bir arama özellikleri kümesi kullanılarak test çerçevesi tarafından bulunur `UIMap.Designer.cs` . Arama özellikleri, denetimin,, ve özellikleri gibi, denetimi tanımlamak için kullanılabilen özellik adlarının ve özellik değerlerinin ad-değer çiftlerini içerir <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> . Arama özellikleri değişmezse, kodlanmış UI testi Kullanıcı arabirimindeki denetimi başarıyla bulur. Arama özellikleri değiştirilirse, kodlanmış UI testlerinde Kullanıcı arabirimindeki denetimleri ve pencereleri bulmak için buluşsal yöntemler uygulayan bir akıllı eşleşme algoritması vardır. Kullanıcı arabirimi değiştirildiğinde, daha önce tanımlanan öğelerin arama özelliklerini değiştirerek bunların bulundıklarından emin olun.

## <a name="what-to-do-if-your-user-interface-changes"></a>Kullanıcı arabiriminiz değişirse Yapılacaklar
 Kullanıcı arabirimleri genellikle geliştirme sırasında değişir. Bu değişikliklerin etkilerini azaltmak için bazı yollar şunlardır:

- Bu denetime başvuran kayıtlı yöntemi bulun ve bu yöntemin eylemlerini yeniden kaydetmek için **KODLANMıŞ UI test oluşturucusunu** kullanın. Mevcut eylemlerin üzerine yazmak için yöntemi için aynı adı kullanabilirsiniz.

- Bir denetimde artık geçerli olmayan bir onaylama işlemi varsa:

  - Onaylama içeren yöntemi silin.

  - Bu yöntemin çağrısını test yönteminden kaldırın.

  - İnce artı düğmesini UI denetimine sürükleyerek yeni bir onaylama ekleyin, UI haritasını açın ve yeni onay ekleyin.

  Kodlanmış UI testlerini kaydetme hakkında daha fazla bilgi için bkz. [kodunuzu test etmek IÇIN UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md).

## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Testin devam edebilmesi için bir arka plan işleminin tamamlaması gerekiyorsa yapmanız gerekenler
 Sonraki UI eylemine devam edebilmeniz için bir işlem bitene kadar beklemeniz gerekebilir. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> , aşağıdaki örnekte olduğu gibi test devam etmeden önce beklemek için kullanabilirsiniz.

```
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
