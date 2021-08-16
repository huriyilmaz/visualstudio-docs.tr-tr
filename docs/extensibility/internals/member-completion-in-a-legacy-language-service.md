---
title: Eski dil hizmetinde üye Tamamlama | Microsoft Docs
description: IntelliSense üye Tamamlama aracı ipucunun eski dil hizmetinde nasıl çalıştığını ve yönetilen paket çerçevesi (MPF) tarafından nasıl desteklendiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: beb0dc40253ddf4280a3cd4854c53151369098a0ef03c1c275769c498570966a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414655"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Üye Tamamlama

IntelliSense üye tamamlama, belirli bir kapsamın bir sınıf, yapı, numaralandırma veya ad alanı gibi olası üyelerinin listesini görüntüleyen bir araç ipucudur. Örneğin, C# ' de, Kullanıcı "This" öğesini ve ardından bir nokta sonra yazdığında, geçerli kapsamdaki sınıfın veya yapının tüm üyelerinin bir listesi kullanıcının seçim yaptığı bir listede sunulur.

Yönetilen paket çerçevesi (MPF) araç ipucu için destek sağlar ve araç ipucunda listeyi yönetebilir; gerekli olan her şey, listede görüntülenen verileri sağlamak için Ayrıştırıcıdan bir işlem olur.

Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-it-works"></a>Nasıl çalıştığı

Aşağıda, MPF sınıfları kullanılarak üye listesinin gösterildiği iki yol verilmiştir:

- Giriş işaretini bir tanımlayıcıya veya bir üye Tamamlama karakterinden sonra, **IntelliSense** menüsünde **Liste üyelerini** seçerek konumlandırın.

- <xref:Microsoft.VisualStudio.Package.IScanner>Tarayıcı, bir üye tamamlanma karakteri algılar ve [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) belirtecinin belirteç tetikleyicisini belirler.

Bir üye tamamlama karakteri, bir sınıf, yapı veya numaralandırma üyesinin takip edilmesinin gerektiğini gösterir. örneğin, C# veya Visual Basic üye tamamlama karakteri bir, `.` C++ ' da karakter a `.` veya a olur `->` . Tetikleyici değeri, üye seçme karakteri tarandığında ayarlanır.

### <a name="the-intellisense-member-list-command"></a>IntelliSense üye listesi komutu

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Komut, sınıfında yöntemine bir çağrı başlatır <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi de, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)'in ayrıştırma nedeni ile Yöntem ayrıştırıcısını çağırır.

Ayrıştırıcı, geçerli konumun bağlamını ve geçerli konumdan hemen önceki belirteci belirler. Bu belirtece bağlı olarak, bildirimlerin bir listesi sunulur. Örneğin, C# ' de, giriş işaretini bir sınıf üyesine konumlandırdıysanız ve **üyeleri Listele**' yi seçerseniz, sınıfının tüm üyelerinin bir listesini alırsınız. Giriş işaretini bir nesne değişkenini izleyen bir dönemden sonra konumlandırdıysanız, nesnenin temsil ettiği sınıfın tüm üyelerinin bir listesini alırsınız. Üye listesi gösterildiğinde bir üyenin giriş işaretine yerleştirilirse, listeden bir üyenin seçilmesi, giriş işaretinin üzerinde bulunduğu üyenin listedeki bir üyesinin yerini almıştır.

### <a name="the-token-trigger"></a>Belirteç tetikleyicisi

[TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) tetikleyicisi, sınıfında yöntemine bir çağrı başlatır <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi, ayrıştırıcının, [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)ayrıştırma nedenine çağrı yaptığı şekilde çağırır. Belirteç tetikleyicisi [TokenTriggers. Matchayraç](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) bayrağını de içeriyorsa, ayrıştırma nedeni, üye seçimini ve küme ayracı vurgulamasını birleştiren [ParseReason. Memberselectandhighlightayraçları](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)olur.

Ayrıştırıcı, geçerli konumun bağlamını ve üyenin karakter seçimini yapmadan önce yazılmış olanları belirler. Bu bilgilerden ayrıştırıcı, istenen kapsamın tüm üyelerinin bir listesini oluşturur. Bu bildirim listesi <xref:Microsoft.VisualStudio.Package.AuthoringScope> , yönteminden döndürülen nesnesinde depolanır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Herhangi bir bildirim döndürülürse, üye Tamamlama aracı ipucu görüntülenir. Araç ipucu, sınıfının bir örneği tarafından yönetilir <xref:Microsoft.VisualStudio.Package.CompletionSet> .

## <a name="enable-support-for-member-completion"></a>Üye tamamlama desteğini etkinleştir

`CodeSense`Herhangi bir IntelliSense işlemini desteklemek için kayıt defteri girdisinin 1 olarak ayarlanmış olması gerekir. Bu kayıt defteri girişi, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dil paketiyle ilişkili Kullanıcı özniteliğine geçirilmiş bir adlandırılmış parametreyle ayarlanabilir. Dil hizmeti sınıfları, bu kayıt defteri girdisinin değerini <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> sınıfındaki özelliğinden okur <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

Tarayıcınız [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)belirteç tetikleyicisini döndürürse ve ayrıştırıcılarınız bildirimlerin listesini döndürürse, üye Tamamlama listesi görüntülenir.

## <a name="support-member-completion-in-the-scanner"></a>Tarayıcıda üye tamamlamayı destekleme

Tarayıcının bir üye tamamlanma karakterini algılayabilmesi ve TokenTriggers 'ın belirteç tetikleyicisini ayarlamanız gerekir [. üyenin](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) bu karakter ayrıştırıldığında seçim yapın.

### <a name="scanner-example"></a>Tarayıcı örneği

İşte, üye tamamlama karakterini algılamaya ve uygun bayrağı ayarlamaya yönelik basitleştirilmiş bir örnek <xref:Microsoft.VisualStudio.Package.TokenTriggers> . Bu örnek yalnızca tanım amaçlıdır. Tarayıcınızın bir `GetNextToken` metin satırından belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar. Örnek kod, her bir doğru karakter türünü gördüğünde tetikleyiciyi yalnızca ayarlar.

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

## <a name="support-member-completion-in-the-parser"></a>Ayrıştırıcıda üye tamamlamayı destekleme

Üye tamamlama için <xref:Microsoft.VisualStudio.Package.Source> sınıfı <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> yöntemini çağırır. Listeyi sınıfından türetilmiş bir sınıfta uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.Declarations> . <xref:Microsoft.VisualStudio.Package.Declarations>Uygulamanız gereken yöntemler hakkındaki ayrıntılar için sınıfına bakın.

Bir üye seçme karakteri yazıldığında ayrıştırıcı, [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) veya [ParseReason. Memberselectandhighlightayraçları](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) ile çağırılır. Nesnede verilen konum, <xref:Microsoft.VisualStudio.Package.ParseRequest> üyenin karakter seçmesini hemen sonra. Ayrıştırıcı, kaynak kodda söz konusu noktada yer alan bir üye listesinde görünebilen tüm üyelerin adlarını toplamalıdır. Ardından ayrıştırıcı, kullanıcının üye seçme karakteri ile ilişkilendirilmesini istediğini kapsamını belirlemek için geçerli satırı ayrıştırmalıdır.

Bu kapsam, üyenin karakter seçimini yapmadan önce tanımlayıcı türünü temel alır. Örneğin, C# ' de, bir türü olan üye değişkeni verildiğinde `languageService` `LanguageService` **LanguageService yazarak.** sınıfın tüm üyelerinin bir listesini oluşturur `LanguageService` . Ayrıca C# ' de şunu yazarak yazın **.** Geçerli kapsamdaki sınıfın tüm üyelerinin bir listesini oluşturur.

### <a name="parser-example"></a>Ayrıştırıcı örneği

Aşağıdaki örnek, bir listeyi doldurmanız için bir yol gösterir <xref:Microsoft.VisualStudio.Package.Declarations> . Bu kod, ayrıştırıcısının bir bildirim oluşturduğu ve sınıf üzerinde bir yöntemi çağırarak onu listeye eklediği varsayılmaktadır `AddDeclaration` `TestAuthoringScope` .

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
