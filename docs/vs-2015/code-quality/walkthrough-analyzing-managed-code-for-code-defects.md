---
title: 'İzlenecek yol: kod kusurları için yönetilen kodu analiz etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609328"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>İzlenecek yol: Kod Kusurları için Yönetilen Kodu Analiz Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, kod hataları için yönetilen bir projeyi kod çözümleme aracını kullanarak analiz edersiniz.

 Bu izlenecek yol, .NET tarafından yönetilen kod derlemelerinizi Microsoft .NET Framework Tasarım kılavuzlarından uyum sağlayacak şekilde çözümlemek için kod analizini kullanma sürecinde size kılavuzluk eder.

 Bu izlenecek yolda şunları yapabilirsiniz:

- Kod hatası uyarılarını çözümleyin ve düzeltin.

## <a name="prerequisites"></a>Ön koşullar

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Sınıf kitaplığı oluşturma

#### <a name="to-create-a-class-library"></a>Bir sınıf kitaplığı oluşturmak için

1. **Dosya** menüsünde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Yeni** ' ye ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Proje türleri**altında, **Visual C#**' ye tıklayın.

3. **Şablonlar**altında, **sınıf kitaplığı**' nı seçin.

4. **Ad** metin kutusuna **CodeAnalysisManagedDemo** yazın ve ardından **Tamam**' a tıklayın.

5. Proje oluşturulduktan sonra, Class1.cs dosyasını açın.

6. Class1.cs içindeki var olan metni şu kodla değiştirin:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Class1.cs dosyasını kaydedin.

## <a name="analyze-the-project"></a>Projeyi çözümle

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Kod kusurları için yönetilen bir projeyi analiz etmek için

1. **Çözüm Gezgini**' de CodeAnalysisManagedDemo projesini seçin.

2. **Proje** menüsünde **Özellikler**' e tıklayın.

     CodeAnalysisManagedDemo özellikleri sayfası görüntülenir.

3. **CodeAnalysis**öğesine tıklayın.

4. **Derlemede Kod analizini etkinleştir (CODE_ANALYSIS sabiti tanımlar**) işaretli olduğundan emin olun.

5. **Bu kural kümesini Çalıştır** açılan listesinden **Microsoft tüm kurallar**' ı seçin.

6. **Dosya** menüsünde, **Seçili öğeleri kaydet**' e tıklayın ve ardından ManagedDemo Özellikleri sayfalarını kapatın.

7. **Yapı** menüsünde, **ManagedDemo oluştur**' a tıklayın.

     CodeAnalysisManagedDemo proje derleme uyarıları, **Kod Analizi** ve **Çıkış** pencereleri içinde raporlanır.

     **Kod Analizi** penceresi görünmezse, **Çözümle** menüsünde **Windows** ' u ve ardından **Kod Analizi**' ni seçin.

## <a name="correct-the-code-analysis-issues"></a>Kod Analizi sorunlarını düzeltin

#### <a name="to-correct-code-analysis-rule-violations"></a>Kod analizi kural ihlallerini düzeltmek için

1. **Görünüm** menüsünde **hata listesi**' a tıklayın.

     Seçtiğiniz geliştirici profiline bağlı olarak, **Görünüm** menüsünde **diğer pencereleri** işaret etmeniz ve ardından **hata listesi**' ne tıklamanız gerekebilir.

2. **Çözüm Gezgini**, **tüm dosyaları göster**' e tıklayın.

3. Sonra, Özellikler düğümünü genişletin ve ardından AssemblyInfo.cs dosyasını açın.

4. Uyarıları düzeltmek için aşağıdakileri kullanın:

- [CA1014: Derlemeleri CLSCompliantAttribute Ile işaretle](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: ' demo ' CLSCompliantAttribute ile işaretlenmelidir ve değeri true olmalıdır.

  - Kodu `using``System;` AssemblyInfo.cs dosyasına ekleyin.

       Sonra, kodu `[assembly: CLSCompliant(true)]` AssemblyInfo.cs dosyasının sonuna ekleyin.

       Projeyi yeniden derleyin.

- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Şu oluşturucuyu bu sınıfa ekleyin: Genel Tanıtım (dize)

  - Oluşturucuyu sınıfına ekleyin `public demo (String s) : base(s) { }` `demo` .

- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Şu oluşturucuyu bu sınıfa ekleyin: public demo (dize, özel durum)

  - Oluşturucuyu sınıfına ekleyin `public demo (String s, Exception e) : base(s, e) { }` `demo` .

- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Şu oluşturucuyu bu sınıfa ekleyin: protected demo (SerializationInfo, StreamingContext)

  - Kodu `using System.Runtime.Serialization;` Class1.cs dosyasının başına ekleyin.

       Sonra, oluşturucuyu ekleyin `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Projeyi yeniden derleyin.

- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Şu oluşturucuyu bu sınıfa ekleyin: public demo ()

  - Oluşturucuyu sınıfına ekleyin `public demo () : base() { }` `demo` **.**

       Projeyi yeniden derleyin.

- [CA1709: tanımlayıcılar doğru şekilde yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: ' testCode ' ad alanı adının büyük küçük harflerini ' testCode ' Ile değiştirerek düzeltin.

  - Ad alanının büyük küçük harflerini `testCode` olarak değiştirin `TestCode` .

- [CA1709: tanımlayıcılar doğru bir şekilde olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: ' demo ' ad alanının büyük küçük harflerini ' demo ' Ile değiştirerek düzeltin.

  - Üyenin adını olarak değiştirin `Demo` .

- [CA1709: tanımlayıcılar doğru şekilde olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: ' Item ' üye adının büyük küçük harflerini ' öğe ' Ile değiştirerek düzeltin.

  - Üyenin adını olarak değiştirin `Item` .

- [CA1710: tanımlayıcıda doğru sonek](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)olmalıdır: Microsoft. Naming: ' testCode. Demo ' öğesini ' Exception ' ile sona erdirmek Için yeniden adlandırın.

  - Sınıfının ve oluşturucularının adını olarak değiştirin `DemoException` .

- [CA2210: derlemeler geçerli tanımlayıcı adlara sahip olmalıdır](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): ' ManagedDemo ' öğesini bir tanımlayıcı ad anahtarıyla imzalayın.

  - **Proje** menüsünde **ManagedDemo özellikleri**' ne tıklayın.

       Proje özellikleri görüntülenir.

       **İmzalama**' ya tıklayın.

       **Derlemeyi imzala** onay kutusunu seçin.

       **Bir dize adı seçin anahtar dosyası** listesinde, öğesini seçin **\<New…>** .

       **Tanımlayıcı ad anahtarı oluştur** iletişim kutusu görüntülenir.

       **Anahtar dosya adı**' nda, TestKey yazın.

       Bir parola girin ve ardından **Tamam**' a tıklayın.

       **Dosya** menüsünde, **Seçili öğeleri kaydet**' e tıklayın ve ardından özellik sayfalarını kapatın.

       Projeyi yeniden derleyin.

- [CA2237: ISerializable türlerini SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: olarak işaretleyin bu tür ISerializable uyguladığından ' demo ' türüne bir [Serializable] özniteliği ekleyin.

  - `[Serializable ()]`Özniteliğini sınıfına ekleyin `demo` .

       Projeyi yeniden derleyin.

  Değişiklikleri tamamladıktan sonra, Class1.cs dosyası aşağıdaki gibi görünmelidir:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Kod Analizi uyarılarını hariç tut

#### <a name="to-exclude-code-defect-warnings"></a>Kod hatası uyarılarını dışlamak için

1. Kalan uyarıların her biri için aşağıdakileri yapın:

   1. Kod Analizi penceresinde, uyarıyı seçin.

   2. **Eylemler**' i seçin, sonra **iletiyi Gizle**' yi seçin ve ardından **Proje gizleme dosyası**' nı seçin.

      Daha fazla bilgi için bkz [. nasıl yapılır: menü öğesini kullanarak uyarıları gösterme](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Projeyi yeniden derleyin.

    Proje herhangi bir uyarı veya hata olmadan oluşturulur.
