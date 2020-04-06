---
title: Eski Dil Hizmetinde Üye Tamamlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707191"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Üye Tamamlama

IntelliSense Üye Tamamlama, sınıf, yapı, numaralandırma veya ad alanı gibi belirli bir kapsamdaki olası üyelerin listesini görüntüleyen bir araç ipucudur. Örneğin, C#'da, kullanıcı bir dönem tarafından "bu" yazarsa, geçerli kapsamdaki sınıfın veya yapının tüm üyelerinin listesi, kullanıcının seçebileceği bir listede sunulur.

Yönetilen paket çerçevesi (MPF), araç ipucu ve takım ipucundaki listeyi yönetme desteği sağlar; gerekli olan tek şey, listede görünen verileri sağlamak için ayrıştırıcıdan işbirliğidir.

Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Editör ve Dil Hizmetlerini Genişletme'ye](../../extensibility/extending-the-editor-and-language-services.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-it-works"></a>Nasıl Çalışır?

Üye listesinin MPF sınıfları kullanılarak gösterildiği iki yol şunlardır:

- Bakıcıyı tanımlayıcıya veya üye tamamlama karakterine yerleştirip **IntelliSense** menüsünden **Liste Üyeleri'ni** seçmek.

- Tarayıcı <xref:Microsoft.VisualStudio.Package.IScanner> bir üye tamamlama karakteri algılar ve bu karakter için [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) bir belirteç tetikleyici ayarlar.

Üye tamamlama karakteri, bir sınıfın, yapının veya numaralandırmanın bir üyesinin izlenmesini gösterir. Örneğin, C# veya Visual Basic'te üye `.`tamamlama karakteri , C++'da ise karakter a `.` veya `->`. Üye seçkarakteri tarandığında tetikleyici değeri ayarlanır.

### <a name="the-intellisense-member-list-command"></a>IntelliSense Üye Listesi Komutu

Komut <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> sınıf ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntem üzerinde yönteme bir çağrı başlatır, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sırayla, [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)ayrıştırıcı nedeni ile yöntem ayrıştırıcı çağırır.

Parser, geçerli konumun bağlamını ve geçerli pozisyonun altında veya hemen öncesindeki belirteci belirler. Bu belirteci temel alın, bildirimlerlistesi sunulur. Örneğin, C#'da, bir sınıf üyesine bakıcıyı konumlandırır ve **Liste Üyeleri'ni**seçerseniz, sınıfın tüm üyelerinin bir listesini alırsınız. Bir nesne değişkenini izleyen bir dönemden sonra caret'i konumlandırarsanız, nesnenin temsil ettiği sınıfın tüm üyelerinin listesini alırsınız. Üye listesi gösterildiğinde, bakıcı bir üyenin üzerinde konumlandırılmışsa, listeden bir üye seçmenin listedeki üyenin yerini alacağına dikkat edin.

### <a name="the-token-trigger"></a>Belirteç Tetikleyicisi

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) tetikleyici <xref:Microsoft.VisualStudio.Package.Source> sınıf ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntem <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> üzerinde yöntem için bir çağrı başlatır, sırayla, [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)ayrıştırıcı nedeni ile ayrıştırıcı çağırır. Belirteç tetikleyicisi ayrıca [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) bayrağını da içeriyorduysa, ayrıştırma nedeni üye seçimi ve ayraç vurgulamayı birleştiren [ParseReason.MemberSelectAndHighlightBraces'tir.](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)

Parser, geçerli konumun bağlamını ve üye karakter seçmeden önce yazılanları belirler. Bu bilgilerden, ayrıştırıcı, istenen kapsamın tüm üyelerinin bir listesini oluşturur. Bu bildirim listesi <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemden döndürülen nesnede depolanır. Herhangi bir bildirim döndürülürse, üye tamamlama aracı ipucu görüntülenir. Araç ipucu <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıfın bir örneği tarafından yönetilir.

## <a name="enable-support-for-member-completion"></a>Üye Tamamlama Için Destek Etkinleştir

Herhangi bir `CodeSense` IntelliSense işlemini desteklemek için kayıt defteri girişini 1 olarak ayarlamanız gerekir. Bu kayıt defteri girişi, dil paketiyle ilişkili <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> kullanıcı özniteliğine geçirilen adlandırılmış bir parametreyle ayarlanabilir. Dil hizmeti sınıfları, bu kayıt defteri <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> girişinin <xref:Microsoft.VisualStudio.Package.LanguagePreferences> değerini sınıftaki özellikten okur.

Tarayıcınız [TokenTriggers.MemberSelect'in](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)belirteç tetikleyicisini döndürürse ve parer'iniz bir bildirim listesi döndürürse, üye tamamlama listesi görüntülenir.

## <a name="support-member-completion-in-the-scanner"></a>Tarayıcıda Üye Tamamlamayı Destekleyin

Tarayıcı bir üye tamamlama karakteri algılamak ve bu karakter ayrıştırılmış zaman [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) belirteç tetikleyici ayarlamak gerekir.

### <a name="scanner-example"></a>Tarayıcı örneği

Burada, üye tamamlama karakterini algılamanın ve uygun <xref:Microsoft.VisualStudio.Package.TokenTriggers> bayrağı ayarlamanın basitleştirilmiş bir örneği verilmiştir. Bu örnek yalnızca açıklayıcı amaçlar içindir. Tarayıcınızın bir metin satırından `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar. Örnek kod, doğru karakter türünü gördüğünde tetikleyiciyi ayarlar.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Parser'da Üye Tamamlamayı Destekleyin

Üye nin tamamlanması <xref:Microsoft.VisualStudio.Package.Source> için <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> sınıf yöntemi çağırır. Listeyi <xref:Microsoft.VisualStudio.Package.Declarations> sınıftan türetilen bir sınıfta uygulamanız gerekir. Uygulamanız <xref:Microsoft.VisualStudio.Package.Declarations> gereken yöntemler le ilgili ayrıntılar için sınıfa bakın.

Ayrıştırıcı, üye seçili karakter yazıldığında [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) veya [ParseReason.MemberSelect.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) ile çağrılır. <xref:Microsoft.VisualStudio.Package.ParseRequest> Nesnede verilen konum, üyenin karakteri seçmesinden hemen sonradır. Ayrıştırıcı, kaynak kodun belirli bir noktasında üye listesinde görünebilecek tüm üyelerin adlarını toplamalıdır. Daha sonra ayrıştırıcı, kullanıcının üye seçkarakteriyle ilişkili olmasını istediği kapsamı belirlemek için geçerli satırı ayrıştırmalıdır.

Bu kapsam, üye karakter seçmeden önce tanımlayıcının türüne dayanır. Örneğin, C#'da, bir `languageService` tür `LanguageService`, yazma dili olan üye değişken göz önüne **alındığındaService.** `LanguageService` sınıfın tüm üyelerinin listesini üretir. Ayrıca C# olarak, **bunu yazarak.** geçerli kapsamda sınıfın tüm üyelerinin bir listesini üretir.

### <a name="parser-example"></a>Parser örneği

Aşağıdaki örnek, bir <xref:Microsoft.VisualStudio.Package.Declarations> listeyi doldurmanın bir yolunu gösterir. Bu kod, arayıcının bir bildirim oluşturduğunu varsayar ve `AddDeclaration` `TestAuthoringScope` sınıfta bir yöntem çağırarak listeye ekler.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
