---
title: Yönetilen koddaki Onaylamalar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 529c19753d09d6335e5c9fc5e839cdb7cd0c118c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745784"
---
# <a name="assertions-in-managed-code"></a>Yönetilen Koddaki Onaylar
Bir onaylama veya `Assert` bildirim, deyimi için bağımsız değişken olarak belirttiğiniz bir koşulu sınar `Assert` . Koşul true olarak değerlendirilirse, hiçbir eylem gerçekleşmez. Koşul false olarak değerlendirilirse onaylama işlemi başarısız olur. Hata ayıklama derlemesi ile çalıştırıyorsanız, programınız kesme moduna girer.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [System. Diagnostics ad alanındaki onaylar](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Debug. onaylama yöntemi](#BKMK_The_Debug_Assert_method)

 [Hata ayıklama. onaylama 'nın yan etkileri](#BKMK_Side_effects_of_Debug_Assert)

 [İzleme ve hata ayıklama gereksinimleri](#BKMK_Trace_and_Debug_Requirements)

 [Onaylama bağımsız değişkenleri](#BKMK_Assert_arguments)

 [Onaylama davranışını özelleştirme](#BKMK_Customizing_Assert_behavior)

 [Yapılandırma dosyalarında onayları ayarlama](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> System. Diagnostics ad alanındaki onaylar
 Visual Basic ve Visual C# ' de, `Assert` <xref:System.Diagnostics.Debug> ad alanındaki veya ' den yöntemini kullanabilirsiniz <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> . <xref:System.Diagnostics.Debug> sınıf yöntemleri programınızın yayın sürümüne dahil değildir, bu nedenle boyutu artırmaz veya sürüm kodunuzun hızını azaltmazlar.

 C++, <xref:System.Diagnostics.Debug> sınıf yöntemlerini desteklemez. Aynı etkiyi, <xref:System.Diagnostics.Trace> koşullu derleme ile, örneğin `#ifdef DEBUG` . `#endif` .. ile kullanarak elde edebilirsiniz.

 [Bu konuda](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Debug. onaylama yöntemi
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>Kodunuzun doğru olması durumunda doğru olması gereken koşulları test etmek için ücretsiz yöntemini kullanın. Örneğin, bir tamsayı bölme işlevi yazdığınızı varsayın. Matematik kuralları tarafından, bölen hiçbir şekilde sıfır olamaz. Bunu bir onaylama işlemi kullanarak test edebilirsiniz:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
    { Debug.Assert ( divisor != 0 );
        return ( dividend / divisor ); }
```

 Hata ayıklayıcı altında bu kodu çalıştırdığınızda, onaylama deyimi değerlendirilir, ancak yayın sürümünde karşılaştırma yapılmaz, bu nedenle ek yük yoktur.

 Aşağıda başka bir örnek verilmiştir. Bir denetleme hesabı uygulayan bir sınıfınız aşağıda gösterildiği gibi:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Hesaptan para göndermeden önce, hesap bakiyesinin, geri almaya hazırlandığı miktarı kapsayacak kadar yeterli olduğundan emin olmak istersiniz. Bakiyeyi denetlemek için bir onaylama işlemi yazabilirsiniz:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>Kodunuzun yayın sürümünü oluşturduğunuzda yöntemine yapılan çağrıların kaybolduğunu unutmayın. Yani, dengeyi denetleyen çağrının yayın sürümünde kaybolması anlamına gelir. Bu sorunu çözmek için, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> yayın sürümünde kaybolmayan ile değiştirmelisiniz:

 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>' A yapılan çağrıların aksine, yayın sürümünüze ek yük eklemek için çağırır <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [Bu konuda](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Hata ayıklama. onaylama 'nın yan etkileri
 Kullandığınızda <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> , içinde herhangi bir kodun, `Assert` kaldırılırsa programın sonuçlarını değiştirmediğinden emin olun `Assert` . Aksi takdirde, yanlışlıkla yalnızca programınızın yayın sürümünde görüntülenen bir hata ortaya çıkabilir. Aşağıdaki örnek gibi işlev veya yordam çağrılarını içeren onaylar hakkında özellikle dikkatli olun:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Bu kullanımı <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ilk bakışta güvenli görünebilir, ancak işlev saymasının her çağrılışında bir sayacı güncelleştirdiğini varsayalım. Yayın sürümünü yapılandırdığınızda, bu yapıya çağrı ortadan kalkar, bu nedenle sayaç güncellenmez. Bu, yan etkisi olan bir işlev örneğidir. Yan etkileri olan bir işleve yapılan çağrıyı ortadan kaldırmak, yalnızca yayın sürümünde görünen bir hata oluşmasına neden olabilir. Bu tür sorunlardan kaçınmak için işlev çağrılarını bir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> deyime yerleştirmeyin. Bunun yerine geçici bir değişken kullanın:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 ' I kullandığınızda bile <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> işlev çağrılarını bir deyimin içine yerleştirmeyi önlemek isteyebilirsiniz `Assert` . Bu tür çağrılar güvenli olmalıdır, çünkü <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> deyimler bir yayın derlemesinde ortadan kaldırılmamalıdır. Ancak, bu tür yapılara Habit olarak engel olursanız kullandığınızda bir hata oluşturmanız daha az olabilir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [Bu konuda](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements"></a> İzleme ve hata ayıklama gereksinimleri
 Sihirbazları kullanarak projenizi oluşturursanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , izleme sembolü hem yayın hem de hata ayıklama yapılandırmalarında varsayılan olarak tanımlanır. Hata ayıklama sembolü varsayılan olarak yalnızca hata ayıklama derlemesi içinde tanımlanır.

 Aksi halde, <xref:System.Diagnostics.Trace> yöntemlerin çalışması için programınızın kaynak dosyanın en üstünde aşağıdakilerden birine sahip olması gerekir:

- `#Const TRACE = True` Visual Basic

- `#define TRACE` Visual C# ve C++ içinde

  Ya da programınızın Izleme seçeneğiyle oluşturulması gerekir:

- `/d:TRACE=True` Visual Basic

- `/d:TRACE` Visual C# ve C++ içinde

  Bir C# veya Visual Basic sürüm derlemesinde hata ayıklama yöntemlerini kullanmanız gerekiyorsa, sürüm yapılandırmanızda hata ayıklama sembolünü tanımlamanız gerekir.

  C++, <xref:System.Diagnostics.Debug> sınıf yöntemlerini desteklemez. Aynı etkiyi, <xref:System.Diagnostics.Trace> koşullu derleme ile, örneğin `#ifdef DEBUG` . `#endif` .. ile kullanarak elde edebilirsiniz. Bu sembolleri ** \<Project> Özellik sayfaları** iletişim kutusunda tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic hata ayıklama yapılandırması Için proje ayarlarını değiştirme](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) veya [bir C veya C++ hata ayıklama yapılandırması Için proje ayarlarını değiştirme](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> Onaylama bağımsız değişkenleri
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> en çok üç bağımsız değişken alın. Zorunlu olan ilk bağımsız değişken, denetlemek istediğiniz durumdur. <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName>Veya <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> yalnızca bir bağımsız değişken kullanırsanız, `Assert` yöntemi koşulu denetler ve sonuç yanlış ise, çağrı yığınının içeriğini **Çıkış** penceresine çıkarır. Aşağıdaki örnek ve gösterir <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> :

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Varsa ikinci ve üçüncü bağımsız değişkenler dize olmalıdır. <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>Ya da <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> iki veya üç bağımsız değişkenle veya ' i çağırırsanız, ilk bağımsız değişken bir durumdur. Yöntemi koşulu denetler ve sonuç yanlış ise ikinci dizeyi ve üçüncü dizeleri verir. Aşağıdaki örnek, <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> iki bağımsız değişkenle birlikte gösterilmektedir ve kullanılır:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 Aşağıdaki örnek ve gösterir <xref:System.Diagnostics.Debug.Assert%2A> <xref:System.Diagnostics.Trace.Assert%2A> :

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [Bu konuda](#BKMK_In_this_topic)

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> Onaylama davranışını özelleştirme
 Uygulamanızı Kullanıcı arabirimi modunda çalıştırırsanız, `Assert` Yöntem başarısız olduğunda **onaylama başarısız** iletişim kutusunu görüntüler. Bir onaylama başarısız olduğunda oluşan eylemler <xref:System.Diagnostics.Debug.Listeners%2A> veya özelliği tarafından denetlenir <xref:System.Diagnostics.Trace.Listeners%2A> .

 Koleksiyona bir <xref:System.Diagnostics.TraceListener> nesne ekleyerek `Listeners` , koleksiyondan bir nesneyi kaldırarak <xref:System.Diagnostics.TraceListener> `Listeners` veya <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> varolan bir yöntemi `TraceListener` farklı şekilde davranması için geçersiz kılarak, çıkış davranışını özelleştirebilirsiniz.

 Örneğin, <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> **onaylama başarısız** iletişim kutusunu görüntülemek yerine bir olay günlüğüne yazmak için yöntemini geçersiz kılabilirsiniz.

 Çıktıyı bu şekilde özelleştirmek için, programınızın bir dinleyici içermesi ve yönteminden kalıtımla almanız <xref:System.Diagnostics.TraceListener> ve geçersiz kılması gerekir <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> .

 Daha fazla bilgi için bkz. [Trace dinleyicileri](/dotnet/framework/debug-trace-profile/trace-listeners).

 [Bu konuda](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Yapılandırma dosyalarında onayları ayarlama
 Kod içinde, program yapılandırma dosyanızda ve onaylama işlemleri yapabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
- [Uygulamaları izleme ve İşaretleme](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)