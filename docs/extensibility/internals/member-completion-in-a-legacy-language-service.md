---
title: Eski Dil Hizmeti HizmetLerinde Üye Tamamlama | Microsoft Docs
description: IntelliSense Üye Tamamlama aracı ipucu'un eski bir dil hizmetlerinde nasıl çalıştığını ve yönetilen paket çerçevesi (MPF) tarafından nasıl desteklen olduğunu öğrenin.
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
ms.openlocfilehash: d101001234906558a4fd223e7691c73bd7fb9302
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049811"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Üye Tamamlama

IntelliSense Üye Tamamlaması; sınıf, yapı, numaralama veya ad alanı gibi belirli bir kapsamın olası üyelerinin listesini görüntüleyen bir araç ipucu. Örneğin, C# içinde, kullanıcı "bunu" ve ardından noktayı okursa, geçerli kapsamda sınıfın veya yapının tüm üyelerinin listesi, kullanıcının seçerek seçenin bir listede görüntülenir.

Yönetilen paket çerçevesi (MPF), araç ipucu için destek sağlar ve araç ipucunda listeyi yönetmeyi sağlar; Tek gereken, ayrıştırıcının listede görünen verileri sağlamak için işbirliği yapmaktır.

Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Düzenleyiciyi ve Dil Hizmetlerini Genişletme.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-it-works"></a>Nasıl Çalışır?

MPF sınıfları kullanılarak bir üye listesinin gösterildiği iki yol aşağıda verilmiştir:

- Bir tanımlayıcıda veya üye tamamlama karakterinden sonra caret konumlandırma ve IntelliSense menüsünden **Üyeleri Listele'yi** seçme. 

- Tarayıcı <xref:Microsoft.VisualStudio.Package.IScanner> bir üye tamamlama karakterini algılar ve bu karakter için [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) belirteç tetikleyicisi ayarlar.

Üye tamamlama karakteri, bir sınıf, yapı veya numaralama üyesinin takip etmek olduğunu gösterir. Örneğin, C# veya Visual Basic tamamlama karakteri , C++ içinde ise `.` karakter bir veya `.` `->` olur. Üye seçme karakteri tarandığında tetikleyici değeri ayarlanır.

### <a name="the-intellisense-member-list-command"></a>IntelliSense Üye Listesi Komutu

Komut, sınıfında ve yönteminde yöntemine bir çağrı başlatarak <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)yönteminin ayrıştırma nedeni ile yöntem ayrıştırıcısını çağrır.

Ayrıştırıcı, geçerli konumun bağlamını ve geçerli konumun altındaki veya hemen önceki belirteci belirler. Bu belirteci temel alarak bir bildirim listesi görüntülenir. Örneğin, C# içinde, caret'i bir sınıf üyesine konumlar ve Üyeleri Listele'yi seçerseniz sınıfın tüm üyelerinin bir listesini alırsiniz.  Caret'i bir nesne değişkeninin ardından gelen bir noktanın ardından konumlandırmak, nesnenin temsil ettiği sınıfın tüm üyelerinin listesini elde edersiniz. Üye listesi gösterildiğinde, caret bir üyede konumlandı ise, listeden bir üye seçmek, caret'in açık olduğu üyenin yerine listede yer alan üyeyi değiştirir.

### <a name="the-token-trigger"></a>Belirteç Tetikleyicisi

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) tetikleyicisi, sınıfında ve yönteminde yöntemine bir çağrı başlatarak <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> [parseReason.MemberSelect ayrıştırıcısını parseReason.MemberSelect nedenini kullanarak ayrıştırıcıyı çağırır.](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) Belirteç tetikleyicisi [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) bayrağını da dahil ettiyseniz ayrıştırmanın nedeni, üye seçimini ve ayraç vurgulamasını birleştiren [ParseReason.MemberSelectAndHighlightBraces'tır.](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)

Ayrıştırıcı, geçerli konumun bağlamını ve üye seçme karakterinden önce ne yazıldı olduğunu belirler. Bu bilgilerden ayrıştırıcı istenen kapsamın tüm üyelerinin listesini oluşturur. Bu bildirim listesi, <xref:Microsoft.VisualStudio.Package.AuthoringScope> yönteminden döndürülen nesnesinde <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> depolanır. Herhangi bir bildirim döndürülürse, üye tamamlama aracı ipucu görüntülenir. Araç ipucu, sınıfının bir örneği tarafından <xref:Microsoft.VisualStudio.Package.CompletionSet> yönetilir.

## <a name="enable-support-for-member-completion"></a>Üye Tamamlama Desteğini Etkinleştirme

Herhangi bir `CodeSense` IntelliSense işlemi desteklemek için kayıt defteri girişinin 1 olarak ayarlanmış olması gerekir. Bu kayıt defteri girdisi, dil paketiyle ilişkili kullanıcı özniteliğine <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> geçirilen adlandırılmış bir parametreyle ayarlanabilirsiniz. Dil hizmeti sınıfları, bu kayıt defteri girişinin değerini sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliğinden <xref:Microsoft.VisualStudio.Package.LanguagePreferences> okur.

Tarayıcınız [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)belirteç tetikleyicisini döndürürse ve ayrıştırıcınız bildirimlerin listesini döndürürse, üye tamamlama listesi görüntülenir.

## <a name="support-member-completion-in-the-scanner"></a>Tarayıcıda Üye Tamamlama desteği

Tarayıcı, bir üye tamamlama karakterini algılayalı ve bu karakter ayrıştırıldığında [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) belirteç tetikleyicisi ayarlayabilecektir.

### <a name="scanner-example"></a>Tarayıcı örneği

Burada üye tamamlama karakterini algılama ve uygun bayrağı ayarlama işlemlerinin basitleştirilmiş bir örneği ve ardından ve ve ardından basitleştirilmiş bir örnek <xref:Microsoft.VisualStudio.Package.TokenTriggers> veılmıştır. Bu örnek yalnızca açıklayıcı amaçlara yöneliktir. Tarayıcınızın, bir metin satırına göre `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayıyor. Örnek kod, doğru türdeki karakteri her gördüğünde tetikleyiciyi ayarlar.

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

## <a name="support-member-completion-in-the-parser"></a>Ayrıştırıcıda Üye Tamamlama desteği

Üye tamamlaması için <xref:Microsoft.VisualStudio.Package.Source> sınıfı yöntemini <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> çağıran. Listesini sınıfından türetilen bir sınıfta <xref:Microsoft.VisualStudio.Package.Declarations> uygulamalı. Uygulaması <xref:Microsoft.VisualStudio.Package.Declarations> gereken yöntemlerle ilgili ayrıntılar için sınıfına bakın.

Ayrıştırıcı, bir üye seçme karakteri yazıldığında [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) veya [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) ile çağrılır. Nesnede verilen <xref:Microsoft.VisualStudio.Package.ParseRequest> konum, üye seçme karakterinden hemen sonradır. Ayrıştırıcı, kaynak kodun belirli bir noktasında bir üye listesinde görünen tüm üyelerin adlarını toplaması gerekir. Ardından ayrıştırıcının, kullanıcının üye seçme karakteriyle ilişkilendirilecek kapsamı belirlemek için geçerli satırı ayrıştırması gerekir.

Bu kapsam, üye seçme karakterinden önce tanımlayıcının türünü temel alan bir kapsamdır. Örneğin, C# dilinde, türüne sahip üye değişkenine göre `languageService` `LanguageService` **languageService yazın.** sınıfının tüm üyelerinin listesini `LanguageService` üretir. Ayrıca C# içinde bunu **yazın.** geçerli kapsamda sınıfın tüm üyelerinin listesini üretir.

### <a name="parser-example"></a>Ayrıştırıcı örneği

Aşağıdaki örnekte, bir listeyi doldurmak için bir yol <xref:Microsoft.VisualStudio.Package.Declarations> gösterir. Bu kod, ayrıştırıcının bir bildirim oluşturur ve sınıfındaki bir yöntemi çağırarak bunu `AddDeclaration` listeye `TestAuthoringScope` ekler.

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
