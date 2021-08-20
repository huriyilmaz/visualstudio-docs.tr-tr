---
title: Kod Hataları ve Hataları için Yönetilen Kodu Analiz Etme | Microsoft Docs
ms.date: 01/29/2018
description: .NET yönetilen kod derlemelerini analiz etmek için eski kod analizini kullanmayı öğrenin. Hataları denetleme ve .NET tasarım yönergeleriyle uyumluluk için bkz.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: b93e0cb2a3b74fe26b60094eb74d010e0b1f77ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122162012"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>adım adım kılavuz: Kod hatalarını bulmak için statik kod analizi kullanma

Bu kılavuzda, eski kod analizini kullanarak yönetilen bir projeyi kod hataları için analiz edersiniz.

Bu makale, .NET tarafından yönetilen kod derlemelerinizi .NET tasarım yönergeleriyle uyumlu olacak şekilde analiz etmek için eski analizi kullanma sürecinde size yol sunar.

## <a name="create-a-class-library"></a>Sınıf kitaplığı oluşturma

1. Sınıf Visual Studio 'i açın ve Sınıf Kitaplığı **(.NET Framework) şablonundan yeni bir proje** oluşturun.

1. Projeye **CodeAnalysisManagedDemo adını girin.**

1. Proje oluşturulduktan sonra *Class1.cs dosyasını* açın.

1. Class1.cs'de var olan metni aşağıdaki kodla değiştirin:

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

## <a name="analyze-the-project-for-code-defects"></a>Projeyi kod hataları için analiz etme

1. içinde CodeAnalysisManagedDemo projesini **Çözüm Gezgini.**

2. Yeni **Project** Özellikler'e **tıklayın.**

   CodeAnalysisManagedDemo özellikleri sayfası görüntülenir.

3. İlke **sekmesini Code Analysis** seçin.

::: moniker range="vs-2017"

4. Derlemede **Etkinleştir'Code Analysis seçildiğinden** emin olun.

5. Bu kuralı **çalıştır kümesi açılan** listesinden Microsoft Tüm **Kurallar'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

4. İkili **çözümleyiciler bölümünde Derlemede** çalıştır'ın **seçili olduğundan emin** olun.

5. Etkin kurallar **açılan** listesinden Microsoft Tüm **Kurallar'ı seçin.**

::: moniker-end

6. Dosya menüsünde **Seçili** Öğeleri **Kaydet'e tıklayın** ve ardından özellikler sayfalarını kapatın.

7. Derleme menüsünde **Kod** **DerlemeAnalysisManagedDemo'ya tıklayın.**

    CodeAnalysisManagedDemo proje derleme uyarıları Hata Listesi **ve Çıkış** **pencerelerde** gösterilir.

## <a name="correct-the-code-analysis-issues"></a>Kod analizi sorunlarını düzeltme

1. Görünüm menüsünde **Hata** **Listesi'ne tıklayın.**

    Seçtiğiniz geliştirici profiline bağlı olarak, Görünüm menüsünde  Diğer Windows'ye işaret  etmek ve ardından Hata Listesi'ne **seçmek zorundayabilirsiniz.**

1. Bu **Çözüm Gezgini** Tüm Dosyaları **Göster'i seçin.**

1. Özellikler düğümünü genişletin ve *ardından AssemblyInfo.cs dosyasını* açın.

1. Uyarıları düzeltmek için aşağıdaki ipuçlarını kullanın:

   [CA1014: Derlemeleri CLSCompliantAttribute](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)ile işaretle: `[assembly: CLSCompliant(true)]` Kodu AssemblyInfo.cs dosyasının sonuna ekleyin.

   [CA1032: Standart özel durum oluşturucularını uygulama:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)oluşturucusu `public demo (String s) : base(s) { }` sınıfına `demo` ekleyin.

   [CA1032: Standart özel durum oluşturucularını uygulama:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)oluşturucusu `public demo (String s, Exception e) : base(s, e) { }` sınıfına `demo` ekleyin.

   [CA1032: Standart özel durum oluşturucularını uygulama:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)Oluşturucuyu `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` sınıf demosüne ekleyin. ayrıca için bir deyimi de `using` eklemeniz <xref:System.Runtime.Serialization?displayProperty=fullName> gerekir.

   [CA1032: Standart özel durum oluşturucularını uygulama:](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)oluşturucusu `public demo () : base() { }` sınıfına `demo` ekleyin.

   [CA1709: Tanımlayıcılar doğru büyük/büyük/büyük](../code-quality/ca1709.md)harfe sahip olmalıdır: Ad alanının büyük/büyük/alt harflerini olarak `testCode` `TestCode` değiştirerek.

   [CA1709: Tanımlayıcılar doğru şekilde büyük/büyük](../code-quality/ca1709.md)harfe sahip olmalıdır: Üyenin adını olarak `Demo` değiştir.

   [CA1709: Tanımlayıcılar doğru şekilde büyük/büyük](../code-quality/ca1709.md)harfe sahip olmalıdır: Üyenin adını olarak `Item` değiştir.

   [CA1710: Tanımlayıcılar](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)doğru son eke sahip olmalıdır: Sınıfın adını ve oluşturucularını olarak `DemoException` değiştirme.

   [CA2237: ISerializable türlerini SerializableAttribute](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)ile işaretle: `[Serializable ()]` sınıfına özniteliğini `demo` ekleyin.

   [CA2210: Derlemeler](../code-quality/ca2210.md)geçerli güçlü adlara sahip olmalıdır: 'CodeAnalysisManagedDemo' imzasını bir güçlü ad anahtarıyla imzalar:

   1. Yeni **Project** **CodeAnalysisManagedDemo Özellikleri'ne tıklayın.**

      Proje özellikleri görüntülenir.

   1. İmzalama **sekmesini** seçin.

   1. Derlemeyi **imzala onay** kutusunu seçin.

   1. Dize **adı anahtar dosyası seçin listesinde öğesini** **\<New>** seçin.

      Güçlü **Ad Anahtarı Oluştur** iletişim kutusu görüntülenir.

   1. Anahtar **dosya adı için** **TestKey girin.**

   1. Bir parola girin ve ardından Tamam'ı **seçin.**

   1. Dosya menüsünde **Seçili** Öğeleri **Kaydet'i seçin** ve ardından özellik sayfalarını kapatın.

   Tüm değişiklikleri tamamlandıktan sonra Class1.cs dosyası aşağıdaki gibi görünüyor:

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

1. Projeyi yeniden oluşturma.

## <a name="exclude-code-analysis-warnings"></a>Kod analizi uyarılarını hariç tut

1. Kalan uyarıların her biri için şunları yapın:

    1. Hata Listesinden **uyarıyı seçin.**

    1. Sağ tıklama menüsünden (bağlam menüsünde) Gizleme Dosyasında   >  **Bastır'ı seçin.**

1. Projeyi yeniden oluşturma.

     Proje herhangi bir uyarı veya hata olmadan derleme.

## <a name="see-also"></a>Ayrıca bkz.

[Yönetilen kod için kod analizi](../code-quality/code-analysis-for-managed-code-overview.md)
