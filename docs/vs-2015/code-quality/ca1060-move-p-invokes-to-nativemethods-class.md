---
title: 'CA1060: P-Invoke öğesini NativeMethods sınıfına taşı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49a693224b6552340d2a01051318842749a84cc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663671"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir yöntem, yönetilmeyen koda erişmek için platform çağırma hizmetleri 'ni kullanır ve **Nativemethod** sınıflarından birinin üyesi değildir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özniteliği kullanılarak işaretlenenler veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Declare` anahtar sözcüğü kullanılarak tanımlanan Yöntemler gibi platform çağırma yöntemleri, yönetilmeyen koda erişin. Bu yöntemler aşağıdaki sınıflardan birinde olmalıdır:

- **NativeMethods** -Bu sınıf, yönetilmeyen kod izni için yığın izlenecek yol göster ' i göstermez. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanmamalıdır.) Bu sınıf, bir yığın yürüme gerçekleştirileceği için her yerde kullanılabilecek yöntemler içindir.

- **SafeNativeMethods** -Bu sınıf, yönetilmeyen kod izni için yığın izlenecek yol gösterir. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanır.) Bu sınıf, herkes tarafından çağrı yapmak için güvenli olan yöntemlere yöneliktir. Yöntemler herhangi bir arayan için zararsız olduğundan, kullanımın güvenli olduğundan emin olmak için bu yöntemlerin çağıranları tam güvenlik incelemesi gerçekleştirmek için gerekli değildir.

- **UnsafeNativeMethods** -Bu sınıf, yönetilmeyen kod izni için yığın izlenecek yol gösterir. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanır.) Bu sınıf potansiyel olarak tehlikeli Yöntemler içindir. Bu yöntemlerin herhangi bir çağırıcısı, kullanımın güvenli olduğundan emin olmak için, yığın ilerlemesinin gerçekleştirilmediğinden emin olmak için tam bir güvenlik incelemesi gerçekleştirmelidir.

  Bu sınıflar `internal` (`Friend`, Visual Basic) olarak tanımlanır ve yeni örneklerin oluşturulmasını engellemek için özel bir Oluşturucu bildirir. Bu sınıflardaki Yöntemler `static` ve `internal` (`Shared` ve `Friend` Visual Basic) olmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yöntemini uygun **NativeMethods** sınıfına taşıyın. Çoğu uygulama için, P/Invoke 'u **NativeMethods** adlı yeni bir sınıfa taşımak yeterlidir.

 Ancak, diğer uygulamalarda kullanmak üzere kitaplıklar geliştiriyorsanız, **SafeNativeMethods** ve **UnsafeNativeMethods**adlı iki diğer sınıfı tanımlamayı göz önünde bulundurmanız gerekir. Bu sınıflar, **NativeMethods** sınıfına benzer; Ancak, **SuppressUnmanagedCodeSecurityAttribute**adlı özel bir öznitelik kullanılarak işaretlenir. Bu öznitelik uygulandığında, çalışma zamanı tam bir yığın gerçekleştirmez ve tüm çağıranların **UnmanagedCode** iznine sahip olduğundan emin olun. Çalışma zamanı normalde bu izni başlangıçta denetler. Denetim gerçekleştirilmediğinden, bu yönetilmeyen yöntemlere yapılan çağrıların performansını önemli ölçüde iyileştirebilir. Ayrıca, bu yöntemleri çağırmak için sınırlı izinleri olan kodun de kullanılmasına olanak sağlar.

 Ancak, bu özniteliği harika bir şekilde kullanmanız gerekir. Yanlış uygulanırsa, ciddi güvenlik etkilerine neden olabilir.

 Yöntemleri uygulama hakkında daha fazla bilgi için bkz. **NativeMethods** örneği, **SafeNativeMethods** example ve **UnsafeNativeMethods** örneği.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir yöntemi bildirir. İhlalin düzeltilmesi için, **RemoveDirectory** p/Invoke yalnızca P/Invoke tutmak üzere tasarlanan uygun bir sınıfa taşınmalıdır.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>NativeMethods örneği

### <a name="description"></a>Açıklama
 **NativeMethods** sınıfı **SuppressUnmanagedCodeSecurityAttribute**kullanılarak işaretlenmemelidir, çünkü içine yerleştirilen P/Invoke, **UnmanagedCode** izni gerektirir. Çoğu uygulama yerel bilgisayardan çalıştığından ve tam güvenle birlikte çalıştığı için, bu genellikle bir sorun değildir. Ancak, yeniden kullanılabilir kitaplıklar geliştiriyorsanız, bir **SafeNativeMethods** veya **UnsafeNativeMethods** sınıfı tanımlamayı göz önünde bulundurmanız gerekir.

 Aşağıdaki örnek, User32. dll ' den **Messagebip** işlevini sarmalayan bir **Interaction. bip** yöntemi gösterir. **Messagebip** P/Invoke, **NativeMethods** sınıfına konur.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>SafeNativeMethods örneği

### <a name="description"></a>Açıklama
 Herhangi bir uygulamaya güvenle açık olabilecek ve herhangi bir yan etkisi olmayan P/Invoke metotları **SafeNativeMethods**adlı bir sınıfa yerleştirilmelidir. İzinleriniz için gereken izinlere sahip değilsiniz ve nereden çağrıldığının üzerine çok dikkat etmeniz gerekmez.

 Aşağıdaki örnek, Kernel32. dll ' den **GetTickCount** işlevini sarmalayan bir **Environment. TickCount** özelliğini gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods örneği

### <a name="description"></a>Açıklama
 Güvenli bir şekilde çağrılamayan ve yan etkileri **UnsafeNativeMethods**adlı bir sınıfa yerleştirilecek olan P/Invoke yöntemleri. Bu yöntemlerin kullanıcıya istem dışı olarak gösterilmediğinden emin olmak için dikkatli bir şekilde denetlenmesi gerekir. Rule [CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçirin](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) bu konuda yardımcı olabilir. Alternatif olarak, yöntemler onları kullandıklarında **UnmanagedCode** yerine talep edilen başka bir izne sahip olmalıdır.

 Aşağıdaki örnekte, User32. dll ' den **ShowCursor** işlevini sarmalayan bir **Cursor. Hide** yöntemi gösterilmektedir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Tasarım Uyarıları](../code-quality/design-warnings.md)
