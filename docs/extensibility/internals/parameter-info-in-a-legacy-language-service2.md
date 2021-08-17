---
title: Eski Dil Hizmeti2 HizmetLerinde Parametre Bilgileri | Microsoft Docs
description: Yöntem eski bir dil hizmetine yazıldı olarak bir yöntem imzasını görüntülemek için IntelliSense Parametre Bilgisi işlemi nasıl destekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4e21d7df425937b3318aeb672a11a22f406a6872e226dc23a285836cd731327d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275469"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Eski dil hizmetlerinde Parametre Bilgileri 2
IntelliSense Parametre Bilgisi, kullanıcı yöntem parametre listesi için parametre listesi başlangıç karakterini (genellikle açık parantez) türetirken bir yöntemin imzasını görüntüleyen bir araç ipucudur. Her parametre girilirken ve parametre ayırıcısı (genellikle virgül) yazıldıkça, araç ipucu sonraki parametreyi kalın olarak gösterecek şekilde güncelleştirilir.

 Yönetilen paket çerçevesi (MPF) sınıfları Parametre Bilgisi araç ipucu yönetimi için destek sağlar. Ayrıştırıcı parametre başlangıcını, parametre sonraki ve parametre bitiş karakterlerini algılamalı ve yöntem imzalarının ve ilişkili parametrelerinin listesini belirtmalıdır.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Düzenleyiciyi ve Dil Hizmetlerini Genişletme.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Ayrıştırıcı, parametre listesi başlangıç karakteri (genellikle bir açık parantez) bulduğunda tetikleyici <xref:Microsoft.VisualStudio.Package.TokenTriggers> değerini ayarlamış olmalıdır. Bir parametre <xref:Microsoft.VisualStudio.Package.TokenTriggers> ayırıcısı (genellikle virgül) bulduğunda bir tetikleyici ayarlaması gerekir. Bu, parametre bilgisi araç ipucu güncelleştirmesine ve sonraki parametreyi kalın olarak göstermesine neden olur. Ayrıştırıcı, parametre listesi bitiş karakterini (genellikle bir kapatma <xref:Microsoft.VisualStudio.Package.TokenTriggers> parantezi) bulduğunda tetikleyici değerini ayarlamış olmalıdır.

 Tetikleyici değeri yöntemine bir çağrı başlatıyor ve bunun üzerine ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırıcısını <xref:Microsoft.VisualStudio.Package.ParseReason> çağırıyor. Ayrıştırıcı parametre listesi başlangıç karakteri öncesinde tanımlayıcının tanınan bir yöntem adı olduğunu belirlerse, nesnesinde eşleşen yöntem imzalarının listesini <xref:Microsoft.VisualStudio.Package.AuthoringScope> döndürür. Herhangi bir yöntem imzası bulunursa, Parametre Bilgisi araç ipucu listede ilk imzayla birlikte görüntülenir. Daha fazla imza yazıldıkça bu araç ipucu güncelleştirilir. Parametre listesi bitiş karakteri yazıldığı zaman Parametre Bilgisi araç ipucu görünümden kaldırılır.

> [!NOTE]
> Parametre Bilgisi araç ipucunda düzgün biçimlendirilen emin olmak için, uygun karakterleri sağlamak için <xref:Microsoft.VisualStudio.Package.Methods> sınıfındaki özellikleri geçersiz kılmanız gerekir. Temel sınıf <xref:Microsoft.VisualStudio.Package.Methods> bir C#stili yöntem imzası varsayıyor. Bunun <xref:Microsoft.VisualStudio.Package.Methods> nasıl yapıla ilgili ayrıntılar için sınıfına bakın.

## <a name="enabling-support-for-the-parameter-info"></a>Parametre Bilgileri için Desteği Etkinleştirme
 Parametre Bilgisi araç ipucu desteklemek için, 'nin `ShowCompletion` adlandırılmış parametresini olarak <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> ayarlayabilirsiniz. `true` Dil hizmeti bu kayıt defteri girişinin değerini özelliğinden <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> okur.

 Ayrıca, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Parametre Bilgisi araç `true` ipucunun göstern için özelliği olarak ayar gerekir.

### <a name="example"></a>Örnek
 Parametre listesi karakterlerini algılamaya ve uygun tetikleyicileri ayarlamaya örnek olarak basitleştirilmiş bir örnek ve burada veılmıştır. Bu örnek yalnızca açıklayıcı amaçlara yöneliktir. Tarayıcınızın, bir metin satırına göre `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayıyor. Örnek kod, doğru türdeki karakteri her gördüğünde tetikleyicileri ayarlar.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Ayrıştırıcıda Parametre Bilgisi Araç İpucu desteği
 Sınıf, <xref:Microsoft.VisualStudio.Package.Source> Parametre Bilgisi araç ipucu görüntülendiğinde ve güncelleştirildiğinde ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıflarının içeriğiyle ilgili bazı <xref:Microsoft.VisualStudio.Package.AuthoringSink> varsayımlar yapar.

- Parametre listesi başlangıç karakteri <xref:Microsoft.VisualStudio.Package.ParseReason> yaz kullanıldığında ayrıştırıcı verilir.

- nesnesinde verilen <xref:Microsoft.VisualStudio.Package.ParseRequest> konum, parametre listesi başlangıç karakterine hemen sonradır. Ayrıştırıcı, o konumdaki tüm yöntem bildirimlerinin imzalarını toplamalı ve bunları nesne sürümünüzde bir listede <xref:Microsoft.VisualStudio.Package.AuthoringScope> depolamalı. Bu liste yöntem adını, yöntem türünü (veya dönüş türünü) ve olası parametrelerin listesini içerir. Bu liste daha sonra Parametre Bilgisi araç ipucunda görüntülenmek için yöntem imzası veya imzaları aranır.

  Ayrıştırıcı daha sonra, girilen yöntemin adını ve kullanıcının parametreler yazarken ne kadar uzakta olduğunu toplamak için nesnesi tarafından belirtilen <xref:Microsoft.VisualStudio.Package.ParseRequest> satırı ayrıştırmalı. Bu, yöntemin adını nesnedeki yöntemine geçirme ve ardından parametre listesi başlangıç karakteri ayrıştırıldı olduğunda yöntemini çağırarak, sonraki parametre listesi ayrıştırıldı olduğunda yöntemini çağırarak ve son olarak parametre listesi bitiş karakteri ayrıştırıldı olduğunda yöntemini çağırarak <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> başarılı <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> olur. Bu yöntem çağrılarının sonuçları, Parametre Bilgisi araç <xref:Microsoft.VisualStudio.Package.Source> ipucuna uygun şekilde güncelleştirmek için sınıfı tarafından kullanılır.

### <a name="example"></a>Örnek
 Kullanıcının gir olabileceği bir metin satırı şu şekildedir. Satırın altındaki sayılar, ayrıştırıcı tarafından satırda bu konumdaki hangi adımın at olduğunu (ayrıştırmanın soldan sağa doğru hareket ettiğinden) işaret eder. Buradaki varsayım, "testfunc" yöntem imzası dahil olmak üzere, satırdan önceki her şeyin yöntem imzaları için ayrıştırılmasıdır.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Ayrıştırıcının attığı adımlar aşağıda özetlenmiştir:

1. Ayrıştırıcı , <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" metniyle çağrır.

2. Ayrıştırıcı çağrısında <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> bulundu.

3. Ayrıştırıcı çağrısında <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> bulundu.

4. Ayrıştırıcı çağrısında <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> bulundu.
