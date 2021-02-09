---
title: Kod kusurları için yönetilen kodu çözümlemek için İzlenecek yol | Microsoft Docs
ms.date: 01/29/2018
description: Eski Kod analizini kullanarak .NET yönetilen kod derlemelerini nasıl analiz edeceğinizi öğrenin. Bkz. hataları denetleme ve .NET tasarım yönergeleriyle uyumluluk.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b9895dc8926f1bb5c7d33e792168ca46297c8196
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859612"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>İzlenecek yol: kod kusurlarını bulmak için statik Kod analizini kullanın

Bu kılavuzda, Eski Kod analizini kullanarak kod kusurları için yönetilen bir proje çözümleyebilirsiniz.

Bu makalede, .NET tarafından yönetilen kod derlemelerinizi .NET tasarım kılavuzlarından uyum sağlamak üzere çözümlemek için eski analizler kullanma sürecinde adım adım açıklanır.

## <a name="create-a-class-library"></a>Sınıf kitaplığı oluşturma

1. Visual Studio 'Yu açın ve **sınıf kitaplığı (.NET Framework)** şablonundan yeni bir proje oluşturun.

1. Projeyi **CodeAnalysisManagedDemo** olarak adlandırın.

1. Proje oluşturulduktan sonra, *Class1.cs* dosyasını açın.

1. Class1.cs içindeki var olan metni şu kodla değiştirin:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Class1.cs dosyasını kaydedin.

## <a name="analyze-the-project-for-code-defects"></a>Kod kusurları için projeyi analiz etme

1. **Çözüm Gezgini**' de CodeAnalysisManagedDemo projesini seçin.

2. **Proje** menüsünde **Özellikler**' e tıklayın.

   CodeAnalysisManagedDemo özellikleri sayfası görüntülenir.

3. **Kod Analizi** sekmesini seçin.

::: moniker range="vs-2017"

4. **Derlemede Kod analizini etkinleştir '** in seçildiğinden emin olun.

5. **Bu kural kümesini Çalıştır** açılan listesinden **Microsoft tüm kurallar**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

4. **İkili çözümleyiciler** bölümünde **derlemede Çalıştır** ' ın seçili olduğundan emin olun.

5. **Etkin kurallar** açılan listesinden **Microsoft tüm kurallar**' ı seçin.

::: moniker-end

6. **Dosya** menüsünde, **Seçili öğeleri kaydet**' e tıklayın ve ardından Özellikler sayfalarını kapatın.

7. **Build** menüsünde **CodeAnalysisManagedDemo oluştur**' a tıklayın.

    CodeAnalysisManagedDemo proje derleme uyarıları **hata listesi** ve **Çıkış** penceresinde gösterilir.

## <a name="correct-the-code-analysis-issues"></a>Kod Analizi sorunlarını düzeltin

1. **Görünüm** menüsünde **hata listesi**' yi seçin.

    Seçtiğiniz geliştirici profiline bağlı olarak, **Görünüm** menüsünde **diğer pencereler** ' i işaret etmeniz ve ardından **hata listesi**' yi seçmeniz gerekebilir.

1. **Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.

1. Özellikler düğümünü genişletin ve ardından *AssemblyInfo.cs* dosyasını açın.

1. Uyarıları düzeltmek için aşağıdaki ipuçlarını kullanın:

   [CA1014: Derlemeleri CLSCompliantAttribute Ile işaretle](/dotnet/fundamentals/code-analysis/quality-rules/ca1014): kodu `[assembly: CLSCompliant(true)]` AssemblyInfo.cs dosyasının sonuna ekleyin.

   [CA1032: Standart özel durum oluşturucuları uygulayın](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): oluşturucuyu `public demo (String s) : base(s) { }` sınıfına ekleyin `demo` .

   [CA1032: Standart özel durum oluşturucuları uygulayın](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): oluşturucuyu `public demo (String s, Exception e) : base(s, e) { }` sınıfına ekleyin `demo` .

   [CA1032: Standart özel durum oluşturucuları uygulayın](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): oluşturucuyu `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` sınıf tanıtımı 'na ekleyin. Ayrıca için bir ifade eklemeniz gerekir `using` <xref:System.Runtime.Serialization?displayProperty=fullName> .

   [CA1032: Standart özel durum oluşturucuları uygulayın](/dotnet/fundamentals/code-analysis/quality-rules/ca1032): oluşturucuyu `public demo () : base() { }` sınıfına ekleyin `demo` .

   [CA1709: tanımlayıcılar doğru şekilde eşit olmalıdır](../code-quality/ca1709.md): ad alanının büyük küçük harflerini olarak değiştirin `testCode` `TestCode` .

   [CA1709: tanımlayıcılar doğru şekilde olmalıdır](../code-quality/ca1709.md): üyenin adını olarak değiştirin `Demo` .

   [CA1709: tanımlayıcılar doğru şekilde olmalıdır](../code-quality/ca1709.md): üyenin adını olarak değiştirin `Item` .

   [CA1710: tanımlayıcılar doğru sonekine sahip olmalıdır](/dotnet/fundamentals/code-analysis/quality-rules/ca1710): sınıfın ve oluşturucularının adını olarak değiştirin `DemoException` .

   [CA2237: ISerializable türlerini SerializableAttribute Ile işaretleyin](/dotnet/fundamentals/code-analysis/quality-rules/ca2237): `[Serializable ()]` özniteliği sınıfına ekleyin `demo` .

   [CA2210: derlemeler geçerli tanımlayıcı adlara sahip olmalıdır](../code-quality/ca2210.md): ' CodeAnalysisManagedDemo ' öğesini bir tanımlayıcı ad anahtarıyla imzalayın:

   1. **Proje** menüsünde **CodeAnalysisManagedDemo özellikleri**' ni seçin.

      Proje özellikleri görüntülenir.

   1. **İmzalama** sekmesini seçin.

   1. **Derlemeyi imzala** onay kutusunu seçin.

   1. **Bir dize adı seçin anahtar dosyası** listesinde, öğesini seçin **\<New>** .

      **Tanımlayıcı ad anahtarı oluştur** iletişim kutusu görüntülenir.

   1. **Anahtar dosya adı** Için **TestKey** girin.

   1. Bir parola girin ve **Tamam**' ı seçin.

   1. **Dosya** menüsünde, **Seçili öğeleri kaydet**' i seçin ve sonra özellik sayfalarını kapatın.

   Tüm değişiklikleri tamamladıktan sonra, Class1.cs dosyası aşağıdaki gibi görünmelidir:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Projeyi yeniden derleyin.

## <a name="exclude-code-analysis-warnings"></a>Kod Analizi uyarılarını hariç tut

1. Kalan uyarıların her biri için aşağıdakileri yapın:

    1. **Hata listesi** uyarıyı seçin.

    1. Sağ tıklama menüsünde (bağlam menüsü),   >  **gizleme dosyasında** Gizle ' yi seçin.

1. Projeyi yeniden derleyin.

     Proje herhangi bir uyarı veya hata olmadan oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

[Yönetilen kod için kod analizi](../code-quality/code-analysis-for-managed-code-overview.md)
