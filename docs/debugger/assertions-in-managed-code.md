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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745784"
---
# <a name="assertions-in-managed-code"></a>Yönetilen Koddaki Onaylar
Bir onaylama veya `Assert` deyimi, `Assert` deyimine bağımsız değişken olarak belirttiğiniz bir koşulu sınar. Koşul true olarak değerlendirilirse, hiçbir eylem gerçekleşmez. Koşul false olarak değerlendirilirse onaylama işlemi başarısız olur. Hata ayıklama derlemesi ile çalıştırıyorsanız, programınız kesme moduna girer.

## <a name="BKMK_In_this_topic"></a>Bu konuda
 [System. Diagnostics ad alanındaki onaylar](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Debug. onaylama yöntemi](#BKMK_The_Debug_Assert_method)

 [Hata ayıklama. onaylama 'nın yan etkileri](#BKMK_Side_effects_of_Debug_Assert)

 [İzleme ve hata ayıklama gereksinimleri](#BKMK_Trace_and_Debug_Requirements)

 [Onaylama bağımsız değişkenleri](#BKMK_Assert_arguments)

 [Onaylama davranışını özelleştirme](#BKMK_Customizing_Assert_behavior)

 [Yapılandırma dosyalarında onayları ayarlama](#BKMK_Setting_assertions_in_configuration_files)

## <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a>System. Diagnostics ad alanındaki onaylar
 Visual Basic ve görselde C#,<xref:System.Diagnostics>ad alanındaki<xref:System.Diagnostics.Debug>ya da<xref:System.Diagnostics.Trace>`Assert`yöntemini kullanabilirsiniz. <xref:System.Diagnostics.Debug> sınıf yöntemleri programınızın yayın sürümüne dahil değildir, bu nedenle boyutu artırmaz veya sürüm kodunuzun hızını azaltmazlar.

 C++<xref:System.Diagnostics.Debug>Sınıfı yöntemlerini desteklemez. Aynı etkiyi, koşullu derleme ile <xref:System.Diagnostics.Trace> sınıfını (`#ifdef DEBUG`... `#endif`gibi) kullanarak elde edebilirsiniz.

 [Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_The_Debug_Assert_method"></a>Debug. onaylama yöntemi
 Kodunuzun doğru olması durumunda doğru tutması gereken koşulları test etmek için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> yöntemini kullanın. Örneğin, bir tamsayı bölme işlevi yazdığınızı varsayın. Matematik kuralları tarafından, bölen hiçbir şekilde sıfır olamaz. Bunu bir onaylama işlemi kullanarak test edebilirsiniz:

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

 Başka bir örnek aşağıda verilmiştir. Bir denetleme hesabı uygulayan bir sınıfınız aşağıda gösterildiği gibi:

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

 Kodunuzun bir yayın sürümünü oluşturduğunuzda <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoduna yapılan çağrıların kaybolduğunu unutmayın. Yani, dengeyi denetleyen çağrının yayın sürümünde kaybolması anlamına gelir. Bu sorunu çözmek için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, yayın sürümünde kaybolmayan <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>ile değiştirmelisiniz:

 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>çağrılarının aksine yayın sürümünüze ek yük eklemek <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> çağırır.

 [Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Side_effects_of_Debug_Assert"></a>Hata ayıklama. onaylama 'nın yan etkileri
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>kullandığınızda, `Assert` kaldırılırsa, `Assert` içindeki herhangi bir kodun programın sonuçlarını değiştirmediğinden emin olun. Aksi takdirde, yanlışlıkla yalnızca programınızın yayın sürümünde görüntülenen bir hata ortaya çıkabilir. Aşağıdaki örnek gibi işlev veya yordam çağrılarını içeren onaylar hakkında özellikle dikkatli olun:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Bu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> kullanımı ilk bakışta güvenli görünebilir, ancak işlev saymasının her çağrılışında bir sayacı güncelleştirdiğini varsayalım. Yayın sürümünü yapılandırdığınızda, bu yapıya çağrı ortadan kalkar, bu nedenle sayaç güncellenmez. Bu, yan etkisi olan bir işlev örneğidir. Yan etkileri olan bir işleve yapılan çağrıyı ortadan kaldırmak, yalnızca yayın sürümünde görünen bir hata oluşmasına neden olabilir. Bu tür sorunlardan kaçınmak için işlev çağrılarını <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ifadeye yerleştirmeyin. Bunun yerine geçici bir değişken kullanın:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>kullandığınızda bile, işlev çağrılarını bir `Assert` bildiriminde yerleştirmeyi önlemek isteyebilirsiniz. Bu tür çağrılar güvenli olmalıdır, çünkü <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> deyimleri bir yayın derlemesinde ortadan kalkar. Ancak, bu tür yapılara Habit olarak engel olursanız, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>kullandığınızda bir hata oluşturmanız daha düşüktür.

 [Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Trace_and_Debug_Requirements"></a>İzleme ve hata ayıklama gereksinimleri
 Projenizi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sihirbazları kullanarak oluşturursanız, Izleme sembolü hem yayın hem de hata ayıklama yapılandırmalarında varsayılan olarak tanımlanır. Hata ayıklama sembolü varsayılan olarak yalnızca hata ayıklama derlemesi içinde tanımlanır.

 Aksi takdirde, <xref:System.Diagnostics.Trace> yöntemlerin çalışması için programınızın kaynak dosyanın en üstünde aşağıdakilerden birine sahip olması gerekir:

- Visual Basic `#Const TRACE = True`

- Görselde C# `#define TRACE` veC++

  Ya da programınızın Izleme seçeneğiyle oluşturulması gerekir:

- Visual Basic `/d:TRACE=True`

- Görselde C# `/d:TRACE` veC++

  Bir C# veya Visual Basic sürüm derlemesinde hata ayıklama yöntemlerini kullanmanız gerekiyorsa, sürüm yapılandırmanızda hata ayıklama sembolünü tanımlamanız gerekir.

  C++<xref:System.Diagnostics.Debug>Sınıfı yöntemlerini desteklemez. Aynı etkiyi, koşullu derleme ile <xref:System.Diagnostics.Trace> sınıfını (`#ifdef DEBUG`... `#endif`gibi) kullanarak elde edebilirsiniz. Bu sembolleri **\<projesi > Özellik sayfaları** iletişim kutusunda tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic hata ayıklama yapılandırması Için proje ayarlarını değiştirme](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) veya [bir C veya C++ hata ayıklama yapılandırması için proje ayarlarını değiştirme](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="BKMK_Assert_arguments"></a>Onaylama bağımsız değişkenleri
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> en fazla üç bağımsız değişken alır. Zorunlu olan ilk bağımsız değişken, denetlemek istediğiniz durumdur. Yalnızca bir bağımsız değişkenle <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> çağırırsanız `Assert` yöntemi koşulu denetler ve sonuç yanlış ise, çağrı yığınının içeriğini **Çıkış** penceresine çıkarır. Aşağıdaki örnekte <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> ve <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>gösterilmektedir:

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Varsa ikinci ve üçüncü bağımsız değişkenler dize olmalıdır. İki veya üç bağımsız değişkenle <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> çağırırsanız, ilk bağımsız değişken bir durumdur. Yöntemi koşulu denetler ve sonuç yanlış ise ikinci dizeyi ve üçüncü dizeleri verir. Aşağıdaki örnek, <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> ve iki bağımsız değişkenle kullanılan <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> gösterir:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 Aşağıdaki örnekte <xref:System.Diagnostics.Debug.Assert%2A> ve <xref:System.Diagnostics.Trace.Assert%2A>gösterilmektedir:

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

## <a name="BKMK_Customizing_Assert_behavior"></a>Onaylama davranışını özelleştirme
 Uygulamanızı Kullanıcı arabirimi modunda çalıştırırsanız `Assert` yöntemi, koşul başarısız olduğunda **onaylama başarısız** iletişim kutusunu görüntüler. Onaylama başarısız olduğunda oluşan eylemler <xref:System.Diagnostics.Debug.Listeners%2A> veya <xref:System.Diagnostics.Trace.Listeners%2A> özelliği tarafından denetlenir.

 Bir <xref:System.Diagnostics.TraceListener> nesnesini `Listeners` koleksiyonuna ekleyerek, `Listeners` koleksiyonundan bir <xref:System.Diagnostics.TraceListener> kaldırarak veya var olan bir <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> farklı davranması için `TraceListener` yöntemini geçersiz kılarak, çıkış davranışını özelleştirebilirsiniz.

 Örneğin, **onaylama başarısız** iletişim kutusunu görüntülemek yerine bir olay günlüğüne yazmak için <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> yöntemini geçersiz kılabilirsiniz.

 Çıktıyı bu şekilde özelleştirmek için programınızın bir dinleyici içermesi ve <xref:System.Diagnostics.TraceListener> ve <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> yöntemini geçersiz kılmanız gerekir.

 Daha fazla bilgi için bkz. [Trace dinleyicileri](/dotnet/framework/debug-trace-profile/trace-listeners).

 [Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Setting_assertions_in_configuration_files"></a>Yapılandırma dosyalarında onayları ayarlama
 Kod içinde, program yapılandırma dosyanızda ve onaylama işlemleri yapabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [İzleme ve İşaretleme Uygulamaları](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)