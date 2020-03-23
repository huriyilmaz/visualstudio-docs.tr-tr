---
title: Kodlu UI Testleri Belirli Olaylar Için Bekleyin olun
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e594a6aec3f9e3a9664c5eac829b27f96f12ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584458"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Kodlanmış UI testlerinin oynatma sırasında belirli olayları beklemesini yapma

Kodlanmış bir UI test oynatma oyununda, teste pencerenin görünmesi, ilerleme çubuğunun kaybolması gibi belirli olayların oluşmasını beklemesi için talimat verebilirsiniz. Bunu yapmak için, aşağıdaki tabloda açıklandığı gibi uygun UITestControl.WaitForControlXXX() yöntemini kullanın. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> Yöntem kullanılarak denetimin etkinleştirilmesini bekleyen kodlanmış bir UI testi örneği [için](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)bkz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

Visual Studio Enterprise

> [!TIP]
> Kodlu UI Test Düzenleyicisi'ni kullanmadan önce de gecikmeler ekleyebilirsiniz. Daha fazla bilgi için [bkz: Kodlanmış Kullanıcı Arabirimi Test Düzenleyicisi'ni kullanarak bir Kullanıcı Arabirimi eyleminden önce gecikme ekleme.](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)

**Uitestcontrol.WaitForControlXXX() Yöntemleri**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Denetimin fare ve klavye girişini kabul etmeye hazır olmasını bekler. Motor, tüm eylemlerin herhangi bir işlemi yapmadan önce denetimin hazır olmasını beklemesi için bu API'yi dolaylı olarak çağırır. Ancak, bazı ezoterik senaryoda, açık arama yapmanız gerekebilir.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Sihirbaz sunucuya arama lar yaparak girişin bazı eşil doğrulamasını yaparken denetimin etkinleştirilmesini bekler. Örneğin, sihirbazın **Sonraki** düğmesinin etkinleştirilmesini beklemek için yöntem leyebilirsiniz (). Bu yöntemin bir örneği için bkz: [Walkthrough: Kodlanmış bir UI testi oluşturma, düzenleme ve bakım.](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Denetimin Ara Birimi'nde görünmesini bekler. Örneğin, uygulama parametrelerin doğrulanmasını yaptıktan sonra bir hata iletişim kutusu bekliyorsunuz. Doğrulama için alınan süre değişkendir. Hata iletişim kutusunu beklemek için bu yöntemi kullanabilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Denetimin ui'den kaybolmasını bekler. Örneğin, ilerleme çubuğunun kaybolmasını bekleyebilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Verilen değere sahip olmak için denetimin belirtilen özelliğini bekler. Örneğin, durum metninin **Bitti**olarak değiştirilmesini beklersiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Denetimin belirtilen özelliğinin belirtilen değerin tam tersi olmasını bekler. Örneğin, edit kutusunun salt okunmamasını, yani editable olmasını beklersiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Belirtilen yüklemin dönmesini `true`bekler. Bu, belirli bir denetimde karmaşık bekleme işlemi (OR koşulları gibi) için kullanılabilir. Örneğin, durum metninin aşağıdaki kodda gösterildiği gibi **Başarılı** veya **Başarısız** olana kadar beklemeniz mümkündür:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);
```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

Önceki tüm yöntemler UITestControl örnek yöntemleridir. Bu yöntem statik bir yöntemdir. Bu yöntem ayrıca belirtilen yüklemin olmasını `true` bekler, ancak birden çok denetimde karmaşık bekleme işlemi (OR koşulları gibi) için kullanılabilir. Örneğin, durum metni **başarılı** olana veya aşağıdaki kodda gösterildiği gibi bir hata iletisi görünene kadar bekleyebilirsiniz:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);
```

Tüm bu yöntemler aşağıdaki davranışa sahiptir:

Bekleme başarılı ve bekleme başarısız olursa yanlış ise yöntemler doğru döndürün.

Bekleme işlemi için örtülü zaman adedi özellik tarafından <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> belirtilir. Bu özelliğin varsayılan değeri 60000 milisaniyedir (bir dakika).

Yöntemler milisaniye içinde açık zaman alacaktır aşırı yükvar. Ancak, bekleme işlemi denetim için örtülü bir arama yla sonuçlandığında veya uygulama meşgul olduğunda, gerçek bekleme süresi belirtilen zaman aramadan daha fazla olabilir.

Önceki işlevler güçlü ve esnektir ve hemen hemen tüm koşulları karşılamalıdır. Ancak, bu yöntemlerin gereksinimlerinizi karşılaması ve kodunuzda bir <xref:System.Threading.Thread.Sleep%2A> veya bir <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>kod yapmanız gerektiğinde, Thread.Sleep() API yerine Oynatma.Wait() yöntemini kullanmanız önerilir. Bunun nedenleri şunlardır:

<xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>Özelliği, uyku süresini değiştirmek için kullanabilirsiniz. Varsayılan olarak, bu değişken 1'dir, ancak kodun üzerindeki bekleme süresini değiştirmek için bu değişkeni artırabilir veya azaltabilirsiniz. Örneğin, özellikle yavaş ağ üzerinden veya başka bir yavaş performans örneği üzerinde test ediyorsanız, bu değişkeni bir yerde (hatta yapılandırma dosyasında) 1,5 olarak değiştirip her yerde %50 ekstra bekleme ekleyebilirsiniz.

Playback.Wait() dahili olarak Thread.Sleep() (yukarıdaki hesaplamadan sonra) kullanıcı iptal\break işlemini denetlerken bir döngü içinde küçük parçalar halinde çağırır. Başka bir deyişle, Playback.Wait() bekleme nin bitiminden önce oynatmayı iptal etmenizi sağlarken, uyku olmayabilir veya özel durum atmayabilir.

> [!TIP]
> Kodlanmış UI Test Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenizi sağlar. Kodlanmış UI Test Düzenleyicisi'ni kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve değiştirebilirsiniz. UI denetim haritasında ui eylemlerini ve bunların ilişkili denetimlerini de edinebilirsiniz. Daha fazla bilgi için [kodlanmış Kullanıcı Arabirimi Test Düzenleyicisi'ni kullanarak kodlanmış Kullanıcı Arabirimi testlerini edit'e](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Walkthrough: Kodlanmış bir UI testi oluşturma, düzenleme ve bakım](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Kodlanmış ui testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Nasıl yapilir: Kodlanmış UI test düzenleyicisini kullanarak bir UI eyleminden önce gecikme ekleme](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
