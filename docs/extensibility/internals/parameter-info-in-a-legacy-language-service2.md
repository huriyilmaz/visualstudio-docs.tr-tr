---
title: Eski Dil Hizmetinde Parametre Bilgisi2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706743"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Parametre Bilgileri
IntelliSense Parametre Bilgisi, kullanıcı yöntem parametre listesi listesi için parametre listesi başlangıç karakterini (genellikle açık bir parantez) yazdığında bir yöntemin imzasını görüntüleyen bir araç ipucudur. Her parametre girilir ve parametre ayırıcı (genellikle virgül) yazılır, araç ucu kalın bir sonraki parametreyi göstermek için güncelleştirilir.

 Yönetilen paket çerçevesi (MPF) sınıfları, Parametre Bilgileri araç ipucunu yönetmek için destek sağlar. Arayıcı, parametre başlangıcını, parametreyi sonraki ve parametre sonu karakterlerini algılamalıdır ve yöntem imzalarının ve bunların ilişkili parametrelerinin bir listesini sağlamalıdır.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Editör ve Dil Hizmetlerini Genişletme'ye](../../extensibility/extending-the-editor-and-language-services.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Bir parametre listesi başlangıç <xref:Microsoft.VisualStudio.Package.TokenTriggers> karakteri (genellikle açık bir parantez) bulduğunda tespçi tetikdeğerini ayarlamak gerekir. Bir parametre <xref:Microsoft.VisualStudio.Package.TokenTriggers> ayırıcı (genellikle virgül) bulduğunda bir tetikleyici ayarlamak gerekir. Bu, Parametre Bilgisi araç ucunun güncelleştirilmesine ve bir sonraki parametrenin kalın olarak gösterilmesine neden olur. Parser parametre listesi <xref:Microsoft.VisualStudio.Package.TokenTriggers> bitiş karakteri (genellikle yakın bir parantez) bulursa tetikleme değerini ayarlamalıdır.

 Tetikleyici <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> değeri, yönteme bir çağrı başlatır ve <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bu da yöntemi ayrıştırıcı olarak <xref:Microsoft.VisualStudio.Package.ParseReason>çağırır. Parser parametre listesi başlangıç karakteri önce tanımlayıcı tanınan bir yöntem adı olduğunu belirlerse, <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnede eşleşen yöntem imzaları listesini döndürür. Herhangi bir yöntem imzası bulunursa, Parametre Bilgileri araç ipucu listedeki ilk imzayla birlikte görüntülenir. Bu araç ucu daha sonra imza daha fazla yazılır olarak güncelleştirilir. Parametre listesi bitiş karakteri yazıldığında, Parametre Bilgileri araç ipucu görünümden kaldırılır.

> [!NOTE]
> Parametre Bilgileri araç ucunun düzgün biçimlendirilmiş olduğundan emin olmak için, <xref:Microsoft.VisualStudio.Package.Methods> uygun karakterleri sağlamak için sınıftaki özellikleri geçersiz kılmanız gerekir. Taban <xref:Microsoft.VisualStudio.Package.Methods> sınıf C#stili yöntem imzasını varsayar. Bunun <xref:Microsoft.VisualStudio.Package.Methods> nasıl yapılabileceğini öğrenmek için sınıfa bakın.

## <a name="enabling-support-for-the-parameter-info"></a>Parametre Bilgileri için Destek Etkinleştirme
 Parametre Bilgisi araç uçlarını desteklemek `ShowCompletion` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> için, `true`'nin adı geçen parametreyi ayarlamanız gerekir. Dil hizmeti, bu kayıt defteri girişinin <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> değerini özellikten okur.

 Buna ek <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> olarak, parametre `true` bilgisi araç ucunun gösterilebilmek için özelliğin ayarlanabilmesi gerekir.

### <a name="example"></a>Örnek
 Burada parametre listesi karakterleri algılama ve uygun tetikleyicileri ayarlama basitleştirilmiş bir örnektir. Bu örnek yalnızca açıklayıcı amaçlar içindir. Tarayıcınızın bir metin satırından `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar. Örnek kod, doğru karakter türünü gördüğünde tetikleyicileri ayarlar.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Parser'daki Parametre Bilgi Araç İpucunun Desteklenmesi
 Parametre <xref:Microsoft.VisualStudio.Package.Source> Bilgisi araç ipucu görüntülendiğinde <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve güncelleştirildiğinde sınıf ve sınıfların içeriği hakkında bazı varsayımlar yapar.

- Parametre listesi <xref:Microsoft.VisualStudio.Package.ParseReason> başlangıç karakteri yazıldığında parser verilir.

- <xref:Microsoft.VisualStudio.Package.ParseRequest> Nesnede verilen konum, parametre listesi başlangıç karakterinden hemen sonradır. Ayrıştırıcı, bu konumda bulunan tüm yöntem bildirimlerinin imzalarını toplamalı ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> bunları nesnenin sürümündeki bir listede depolamalıdır. Bu liste yöntem adı, yöntem türü (veya iade türü) ve olası parametrelerin listesini içerir. Bu liste daha sonra Parametre Bilgileri araç ipucunda görüntülenecek yöntem imzası veya imzaları için aranır.

  Ayrıştırıcı daha sonra girilen <xref:Microsoft.VisualStudio.Package.ParseRequest> yöntemin adını yanı sıra kullanıcının parametreleri yazma da ne kadar boyunca toplamak için nesne tarafından belirtilen satırı ayrıştırmak gerekir. Bu, yöntemin <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> adını <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesneüzerindeki yönteme geçirerek ve parametre <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> listesi başlangıç karakteri ayrıştırıldığında yöntemi çağırarak, parametre listesi sonraki karakter ayrıştırıldığında <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> yöntemi çağırarak ve son olarak parametre listesi bitiş karakteri ayrıştırıldığında yöntemi çağırarak gerçekleştirilir. Bu yöntem çağrılarının <xref:Microsoft.VisualStudio.Package.Source> sonuçları, Parametre Bilgileri araç ucunu uygun şekilde güncelleştirmek için sınıf tarafından kullanılır.

### <a name="example"></a>Örnek
 Burada, kullanıcının girebileceği bir metin satırı verebilirsiniz. Çizginin altındaki sayılar, satırdaki o konumda ki parser tarafından hangi adımın atını gösterir (ayrıştırma soldan sağa doğru hareket eder varsayarak). Burada varsayım satır önce her şey zaten "testfunc" yöntemi imza dahil olmak üzere yöntem imzaları için ayrıştırılmış olmasıdır.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Ayrıştırıcının attığı adımlar aşağıda özetlenmiştir:

1. Parser metin <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" ile çağırır.

2. Ayrıştırıcı <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>çağırır.

3. Ayrıştırıcı <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>çağırır.

4. Ayrıştırıcı <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>çağırır.
