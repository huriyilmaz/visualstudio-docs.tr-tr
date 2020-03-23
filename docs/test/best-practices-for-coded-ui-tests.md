---
title: Kodlanmış UI Testleri için En İyi Yöntemler
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e71029a185d1b3fea1812b2a4b1cf7bf20effff8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565168"
---
# <a name="best-practices-for-coded-ui-tests"></a>Kodlanmış Ara Birimi testleri için en iyi uygulamalar

Bu konu, kodlanmış UI testleri geliştirmek için bazı önerileri açıklar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>En iyi uygulamalar

Esnek kodlanmış bir UI testi oluşturmak için aşağıdaki yönergeleri kullanın.

- **Kodlanmış UI Test Oluşturucu'yu** mümkün olduğunca kullanın.

- *UIMap.designer.cs* dosyasını doğrudan değiştirmeyin. Dosyayı değiştirirseniz, dosyadaki değişiklikler üzerine yazılır.

- Kaydedilmiş yöntemler dizisi olarak testinizi oluşturun. Yöntemin nasıl kaydedilen hakkında daha fazla bilgi için [kodlanmış Kullanıcı Arabirimi testleri oluşturma bilgisine](../test/use-ui-automation-to-test-your-code.md)bakın.

- Kaydedilen her yöntem tek bir sayfa, form veya iletişim kutusunda hareket etmelidir. Her yeni sayfa, form veya iletişim kutusu için yeni bir test yöntemi oluşturun.

- Bir yöntem oluşturduğunuzda, varsayılan ad yerine anlamlı bir yöntem adı kullanın. Anlamlı bir ad yöntemin amacını belirlemeye yardımcı olur.

- Mümkün olduğunda, kaydedilen her yöntemi 10'dan az eylemle sınırlayın. Bu modüler yaklaşım, ui değişirse bir yöntemin değiştirilmesini kolaylaştırır.

- UIMap.Designer.cs *dosyasına* otomatik olarak bir seves yöntemi ekleyen **Kodlanmış UI Test Oluşturucusu'nu**kullanarak her bir seveği oluşturun.

- Kullanıcı arabirimi (UI) değişirse, test yöntemlerini veya sevecyöntemlerini yeniden kaydedin veya varolan bir test yönteminin etkilenen bölümlerini yeniden kaydedin.

- Test altında uygulamanızdaki her modül için ayrı bir [UIMap](/previous-versions/dd580454(v=vs.140)) dosyası oluşturun. Daha fazla bilgi için bkz: [Birden çok Kullanıcı Arabirimi eşlemi içeren büyük bir uygulamayı sınama.](../test/testing-a-large-application-with-multiple-ui-maps.md)

- Test altındaki uygulamada, Kullanıcı Bira denetimleri oluştururken anlamlı adlar kullanın. Anlamlı adlar kullanmak, otomatik olarak oluşturulan denetim adlarına daha fazla netlik ve kullanılabilirlik sağlar.

- API ile kodlayarak iddialar oluşturuyorsanız, [uimap](/previous-versions/dd580454(v=vs.140)) sınıfının *UIMap.cs* dosyasındaki bölümündeki her bir iddia için bir yöntem oluşturun. İddiayı yürütmek için, bu yöntemi test yönteminizden arayın.

- API ile doğrudan kodlarsanız, kodunuzda *UIMap.Designer.cs* dosyasında oluşturulan sınıflardaki özellikleri ve yöntemleri olabildiğince kullanın. Bu sınıflar işinizi daha kolay, daha güvenilir hale getirecek ve daha üretken olmanıza yardımcı olacaktır.

Kodlanmış Kullanıcı Arabirimi testleri, kullanıcı arabirimindeki birçok değişikme otomatik olarak uyum sağlar. Örneğin, bir UI öğesi konumunu veya rengini değiştirmişse, çoğu zaman kodlanmış UI testi doğru öğeyi bulmaya devam edecektir.

Bir test çalışması sırasında, UI denetimleri bir dizi arama özellikleri kullanılarak test çerçevesi tarafından konumlanır. Arama özellikleri, UIMap.Designer.cs dosyasındaki **Kodlanmış UI Test Oluşturucusu** tarafından oluşturulan tanımlardaki her denetim *sınıfına* uygulanır. Arama özellikleri, denetim , ve denetim özellikleri gibi <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>denetimi tanımlamak için kullanılabilecek özellik adları ve <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> özellik değerlerinin ad değeri çiftleri içerir. Arama özellikleri değişmezse, kodlanmış UI testi ui denetimi başarıyla bulur. Arama özellikleri değiştirilirse, kodlanmış Kullanıcı Arabirimi testleri, Kullanıcı Arabirimi'ndeki denetimleri ve pencereleri bulmak için sezgisel olarak uygulayan akıllı eşleştirme algoritmasına sahiptir. UI değiştiğinde, daha önce tanımlanmış öğelerin arama özelliklerini değiştirerek bunların bulunduğundan emin olabilirsiniz.

## <a name="if-your-user-interface-changes"></a>Kullanıcı arabiriminiz değişirse

Kullanıcı arabirimleri geliştirme sırasında sık sık değişir. Bu değişikliklerin etkisini azaltmanın bazı yolları şunlardır:

- Bu denetime başvuran kayıtlı yöntemi bulun ve bu yönteme yönelik eylemleri yeniden kaydetmek için **Kodlanmış UI Test Oluşturucusu'nu** kullanın. Varolan eylemlerin üzerine yazmak için yöntem için aynı adı kullanabilirsiniz.

- Denetimde artık geçerli olmayan bir iddia varsa:

  - İddiayı içeren yöntemi silin.

  - Bu yönteme yapılan çağrıyı test yönteminden kaldırın.

  - Çapraz saç düğmesini UI denetimine sürükleyerek yeni bir iddia ekleyin, UI eşlemasını açın ve yeni iddiayı ekleyin.

Kodlanmış Kullanıcı Arabirimi testlerini kaydetme hakkında daha fazla bilgi için [kodunuzu test etmek için Kullanıcı Arabirimi otomasyonunu kullanın'a](../test/use-ui-automation-to-test-your-code.md)bakın.

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Test devam etmeden önce bir arka plan işleminin tamamlanması gerekiyorsa

Bir sonraki UI eylemine devam etmeden önce bir işlemin tamamlanmasını beklemeniz gerekebilir. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> aşağıdaki örnekte olduğu gibi, test devam etmeden önce beklemek için kullanabilirsiniz:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uımap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlu UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Birden çok Kullanıcı Altı Bilgi Har(R)'li büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
