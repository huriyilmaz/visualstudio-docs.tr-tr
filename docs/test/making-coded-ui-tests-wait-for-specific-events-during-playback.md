---
title: Kodlanmış UI testlerinin belirli olayları beklemesini sağlama
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea0bd0135ca90f96c2275248da7d116ecfd92e01
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286784"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Kayıttan yürütme sırasında belirli olaylar için kodlanmış UI testlerinin beklemesini sağlama

Kodlanmış bir UI Testi Kayıttan yürütmede, teste bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek için teste talimat verebilirsiniz. Bunu yapmak için, aşağıdaki tabloda açıklandığı gibi uygun UITestControl. WaitForControlXXX () metodunu kullanın. Yöntemi kullanılarak bir denetimin etkinleştirilmesini bekleyen kodlanmış UI testinin bir örneği için <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> bkz. [izlenecek yol: KODLANMıŞ bir UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

Visual Studio Enterprise

> [!TIP]
> Ayrıca, kodlanmış UI test düzenleyicisini kullanarak eylemlerin önüne gecikme ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: KODLANMıŞ UI test düzenleyicisini kullanarak bir kullanıcı arabirimi eyleminden önce gecikme ekleme](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action).

**Uııtemstcontrol. WaitForControlXXX () yöntemleri**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Denetimin, fare ve klavye girişini kabul etmeye hazırmasını bekler. Motor herhangi bir işlem yapmadan önce denetimin hazırlanmasını beklemek için tüm eylemler için bu API 'YI örtülü olarak çağırır. Ancak, bazı esoteric senaryosunda açık çağrı yapmanız gerekebilir.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Sihirbaz sunucuya çağrılar yaparak girişin zaman uyumsuz doğrulamasını yaparken denetimin etkinleştirilmesini bekler. Örneğin, sihirbazın bir **sonraki** düğmesinin etkinleştirilmesini beklemek için yöntemini () kullanabilirsiniz. Bu yöntemin bir örneği için bkz. [Izlenecek yol: kodlanmış BIR UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Denetimin kullanıcı arabiriminde görünmesini bekler. Örneğin, uygulama parametrelerin doğrulanmasını tamamladıktan sonra bir hata iletişim kutusu bekliyor. Doğrulama için geçen süre değişkendir. Hata iletişim kutusunu beklemek için bu yöntemi kullanabilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Denetimin kullanıcı arabiriminden kaybolması için bekler. Örneğin, ilerleme çubuğunun kaybolmasını bekleyebilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Denetimin belirtilen özelliğinin verilen değere sahip olmasını bekler. Örneğin, durum metninin tamamlanmasını **bekleyin.**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Denetimin belirtilen özelliğinin belirtilen değerin tersi olmasını bekler. Örneğin, düzenleme kutusunun salt okunurdur, diğer bir deyişle düzenlenebilir olmasını bekleyebilirsiniz.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Belirtilen koşulun olarak dönüşmesini bekler `true` . Bu, belirli bir denetimdeki karmaşık bekleme işlemi (veya koşullar gibi) için kullanılabilir. Örneğin, aşağıdaki kodda gösterildiği gibi durum metni **başarılı** veya **başarısız** olana kadar bekleyebilirsiniz:

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

Önceki tüm yöntemler UITestControl örnek yöntemleridir. Bu yöntem, statik bir yöntemdir. Bu yöntem ayrıca, belirtilen koşulun olmasını bekler, `true` ancak birden fazla denetim üzerinde karmaşık bekleme işlemi (veya koşullar gibi) için kullanılabilir. Örneğin, aşağıdaki kodda gösterildiği gibi, durum metni **başarılı** olana veya bir hata iletisi görünene kadar bekleyebilirsiniz:

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

Bu yöntemler, bekleme başarılı olursa true, bekleme başarısız olursa false döndürür.

Bekleme işlemi için örtük zaman aşımı, özelliği tarafından belirtilir <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> . Bu özelliğin varsayılan değeri 60000 milisaniyedir (bir dakika).

Metotlarda, zaman aşımı süresi (milisaniye) olan bir aşırı yükleme vardır. Ancak, bekleme işlemi denetim için örtük bir aramaya neden olduğunda veya uygulama meşgul olduğunda, gerçek bekleme süresi belirtilen zaman aşımından daha fazla olabilir.

Önceki işlevler güçlü ve esnektir ve neredeyse tüm koşulları karşılamalıdır. Bununla birlikte, bu yöntemlerin gereksinimlerinizi karşılamadığı durumlarda ve kodunuzda bir veya bir olarak kod oluşturmanız gerekiyorsa <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> <xref:System.Threading.Thread.Sleep%2A> , Thread. Sleep () API yerine playback. Wait () kullanmanız önerilir. Bunun nedenleri şunlardır:

<xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>Uyku süresini değiştirmek için özelliğini kullanabilirsiniz. Bu değişken varsayılan olarak 1 ' dir, ancak tüm kod üzerinde bekleme süresini değiştirmek için onu artırabilir veya azaltabilirsiniz. Örneğin, yavaş ağ üzerinden özel olarak test ediyorsanız veya başka bir performans durumu varsa, her yerde %50 ekstra wait eklemek için bu değişkeni tek bir yerde (veya yapılandırma dosyasında bile) 1,5 olarak değiştirebilirsiniz.

Playback. Wait (), Kullanıcı cancel\break işlemini denetlerken bir for döngüsünde Iş parçacığı. Sleep () öğesini (hesaplamadan sonra) bir for döngüsünde daha küçük parçalara göre dahili olarak çağırır. Diğer bir deyişle oynatma. Wait (), bekleme sonundan önce kayıttan yürütmeyi iptal etmenizi sağlar, ancak işlem özel durum oluşturmaz.

> [!TIP]
> Kodlanmış UI Testi Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI test düzenleyicisini kullanarak test yöntemlerinizi bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. UI eylemlerini ve bunlarla ilişkili denetimleri kullanıcı arabirimi denetim eşlemesinde da düzenleyebilirsiniz. Daha fazla bilgi için bkz. [kodlanmış UI test düzenleyicisini kullanarak KODLANMıŞ UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenlememe ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Kodlanmış UI testinin anatomumu](../test/anatomy-of-a-coded-ui-test.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Nasıl yapılır: kodlanmış UI test düzenleyicisini kullanarak bir kullanıcı arabirimi eyleminden önce gecikme ekleme](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
