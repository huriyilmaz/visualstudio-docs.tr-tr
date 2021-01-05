---
title: Eski dilde parametre bilgisi Service2 | Microsoft Docs
description: Yöntem bir eski dil hizmetinde yazıldığında yöntem imzasını görüntülemek için IntelliSense parametre bilgisi işlemini nasıl destekleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc239d5b0d580d420683c6940ac2bbd5198335d7
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875953"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Eski dil hizmetinde parametre bilgisi 2
IntelliSense parametre bilgisi, Kullanıcı parametre listesi başlangıç karakterini (genellikle açık bir parantez), yöntem parametre listesi için yazdığında bir yöntemin imzasını görüntüleyen bir araç ipucudur. Her parametre girildiği ve parametre ayırıcısı (genellikle virgül) yazıldığında araç ipucu, sonraki parametreyi kalın olarak göstermek için güncelleştirilir.

 Yönetilen paket çerçevesi (MPF) sınıfları, parametre bilgisi araç ipucunu yönetmek için destek sağlar. Ayrıştırıcı, parametre başlangıcını, sonraki parametreyi ve parametre bitiş karakterlerini algılamamalıdır ve Yöntem imzalarının ve bunlarla ilişkili parametrelerin bir listesini sağlaması gerekir.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Ayrıştırıcı, <xref:Microsoft.VisualStudio.Package.TokenTriggers> bir parametre listesi başlangıç karakteri (genellikle açık parantez) bulduğunda tetikleyici değeri ayarlanmalıdır. Bir <xref:Microsoft.VisualStudio.Package.TokenTriggers> parametre ayırıcısı bulduğunda bir tetikleyici ayarlaması gerekir (genellikle virgül). Bu, bir parametre bilgisi araç ipucunun güncelleştirilmesini sağlar ve sonraki parametreyi kalın olarak gösterir. Ayrıştırıcı, <xref:Microsoft.VisualStudio.Package.TokenTriggers> parametre listesi bitiş karakterini (genellikle bir kapatma parantezi) bulursa tetikleyici değerini ayarlayabilmelidir.

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>Tetikleyici değeri, yöntemi için bir çağrı başlatır <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> , bu da <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntem ayrıştırıcısının ayrıştırma nedenine çağırır <xref:Microsoft.VisualStudio.Package.ParseReason> . Ayrıştırıcı, parametre listesi başlangıç karakterinden önceki tanımlayıcının tanımlayıcı bir yöntem adı olduğunu belirlerse, nesnedeki eşleşen Yöntem imzalarının bir listesini döndürür <xref:Microsoft.VisualStudio.Package.AuthoringScope> . Herhangi bir yöntem imzası bulunursa, parametre bilgisi araç ipucu listedeki ilk imzayla birlikte görüntülenir. Daha fazla imza yazıldığı için bu araç ipucu güncellenir. Parametre listesi bitiş karakteri yazıldığında, parametre bilgisi araç ipucu görünümden kaldırılır.

> [!NOTE]
> Parametre bilgisi araç ipucunun düzgün biçimlendirildiğinden emin olmak için, <xref:Microsoft.VisualStudio.Package.Methods> uygun karakterleri sağlamak üzere sınıfındaki özellikleri geçersiz kılmanız gerekir. Temel <xref:Microsoft.VisualStudio.Package.Methods> sınıf, bir C# stili yöntem imzasını varsayar. <xref:Microsoft.VisualStudio.Package.Methods>Bunun nasıl yapılabileceği hakkında ayrıntılı bilgi edinmek için sınıfına bakın.

## <a name="enabling-support-for-the-parameter-info"></a>Parametre bilgisi için destek etkinleştiriliyor
 Parametre bilgileri araç ipuçlarını desteklemek için `ShowCompletion` , öğesinin adlandırılmış parametresini olarak ayarlamanız gerekir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . Dil hizmeti, bu kayıt defteri girişinin değerini <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliğinden okur.

 Ayrıca, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> `true` parametre bilgisi araç ipucunun gösterilmesi için özelliği olarak ayarlanmalıdır.

### <a name="example"></a>Örnek
 Burada parametre listesi karakterlerini algılamaya ve uygun Tetikleyicileri ayarlamaya yönelik basitleştirilmiş bir örnek verilmiştir. Bu örnek yalnızca tanım amaçlıdır. Tarayıcınızın bir `GetNextToken` metin satırından belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar. Örnek kod, her bir doğru karakter türünü gördüğünde yalnızca Tetikleyicileri ayarlar.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Ayrıştırıcıda parametre bilgisi araç Ipucunu destekleme
 <xref:Microsoft.VisualStudio.Package.Source>Sınıfı, <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> parametre bilgisi araç ipucu görüntülenirken ve güncelleştirilirken, ve sınıflarının içerikleri hakkında bazı varsayımlar yapar.

- Ayrıştırıcı, <xref:Microsoft.VisualStudio.Package.ParseReason> parametre listesi başlangıç karakteri yazıldığında verilir.

- Nesnede verilen konum, <xref:Microsoft.VisualStudio.Package.ParseRequest> parametre listesinin başlangıç karakterinden hemen sonra olur. Ayrıştırıcı, bu konumda bulunan tüm yöntem bildirimlerinin imzalarını toplamalıdır ve bunları nesne sürümünüze bir listede depolar <xref:Microsoft.VisualStudio.Package.AuthoringScope> . Bu liste, yöntem adı, yöntem türü (veya dönüş türü) ve olası parametrelerin bir listesini içerir. Bu liste daha sonra parametre bilgisi araç ipucunda görüntülenecek Yöntem imzası veya imzaları için aranır.

  Ayrıştırıcı daha sonra, <xref:Microsoft.VisualStudio.Package.ParseRequest> girilen yöntemin adını ve kullanıcının ne kadar çok parametre yazmakta olduğunu toplamak için nesne tarafından belirtilen satırı ayrıştırmalıdır. Bu, yönteminin adının <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> nesne üzerindeki yöntemine geçirilmesi <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve sonra <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> parametre listesi başlangıç karakteri ayrıştırıldığında yöntemi çağırmak, <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> sonraki karakter parametre listesi ayrıştırıldığında yöntemi çağırmak ve sonra <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> parametre listesi bitiş karakteri ayrıştırıldığında yöntemi çağırılarak gerçekleştirilir. Bu yöntem çağrılarının sonuçları, <xref:Microsoft.VisualStudio.Package.Source> sınıf tarafından parametre bilgisi araç ipucunu uygun şekilde güncelleştirmek için kullanılır.

### <a name="example"></a>Örnek
 Kullanıcının girebileceğini bir metin satırı aşağıda verilmiştir. Satırın altındaki sayılar, bu konumdaki bu konumdaki ayrıştırıcı tarafından hangi adımın alındığını gösterir (ayrıştırma, soldan sağa kaymakta olduğu varsayıldığında). Buradaki varsayım, satırdaki "testfunc" Yöntem imzası dahil olmak üzere yöntem imzaları için önceden ayrıştırılmasından sonraki şeydir.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Ayrıştırıcısının aldığı adımlar aşağıda özetlenmiştir:

1. Ayrıştırıcı <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" metniyle çağırır.

2. Ayrıştırıcı çağırır <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Ayrıştırıcı çağırır <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Ayrıştırıcı çağırır <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
