---
title: Dil sunucusu protokolüne genel bakış | Microsoft Docs
description: Dil sunucusu protokolünün, dil özelliklerinin çeşitli araçlara sunulmasını sağlayan yararlı bir çerçeve nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d642d1168cbd2a8bd7abadbcdbd7c1e2851b00e
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616136"
---
# <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

## <a name="what-is-the-language-server-protocol"></a>Dil sunucusu protokolü nedir?

Kaynak kodu otomatik tamamlama gibi zengin düzenleme özelliklerini destekleme veya bir düzenleyicide veya IDE 'de bir programlama dilinin **tanımına git** , geleneksel olarak çok zor ve zaman alabilir. Genellikle, düzenleyicinin veya IDE 'nin programlama dilinde bir etki alanı modelinin (tarayıcı, ayrıştırıcı, tür denetleyicisi, Oluşturucu ve daha fazlasını) yazılmasını gerektirir. Örneğin, tutulma IDE 'nin kendisi Java 'da yazıldığı için IDE 'de C/C++ desteği sağlayan, tutulma CDT eklentisi Java dilinde yazılmıştır. Bu yaklaşımdan sonra, Visual Studio için TypeScript kodda C/C++ etki alanı modelinin ve Visual Studio Için C# ' de ayrı bir etki alanı modelinin uygulanması anlamına gelir.

Bir geliştirme aracının dile özgü mevcut kitaplıkları yeniden kullanabilmesi durumunda dile özgü etki alanı modellerinin oluşturulması da çok daha kolaydır. Ancak, bu kitaplıklar genellikle programlama dilinde uygulanır (örneğin, iyi C/C++ etki alanı modelleri C/C++ ' da uygulanır). C/C++ kitaplığını TypeScript 'te yazılmış bir düzenleyiciye tümleştirmek teknik açıdan olasıdır ancak zor olur.

### <a name="language-servers"></a>Dil sunucuları

Başka bir yaklaşım ise kitaplığı kendi sürecinde çalıştırmak ve BT ile iletişim kurmak için işlem arası iletişimi kullanmaktır. Geri gönderilen iletiler bir protokol oluşturur. Dil sunucusu Protokolü (LSP), bir geliştirme aracı ve bir dil sunucusu işlemi arasında değiş tokuş eden iletileri standartlaştırın ürünüdür. Dil sunucularını veya Demons 'yi kullanmak yeni veya önemli bir fikir değildir. VIM ve Emacs gibi düzenleyiciler, anlam otomatik tamamlama desteği sağlamak için bir süredir bunu yapıyor. LSP 'nin hedefi, bu tür tümleştirmeleri basitleştirecek ve dil özelliklerinin çeşitli araçlara sunulmasını sağlayacak yararlı bir çerçeve sunmaktır.

Ortak bir protokole sahip olmak, dilin etki alanı modelinin mevcut bir uygulamasını yeniden kullanarak dil özelliklerinin, en az Fuss ile bir geliştirme aracında tümleştirilmesine olanak tanır. Bir dil sunucusu arka ucu PHP, Python veya Java 'da yazılabilir ve LSP, çeşitli araçlarla kolayca tümleştirilebilmesine olanak sağlar. Protokol ortak bir soyutlama düzeyinde çalışarak bir araç, temel alınan etki alanı modeline özgü duymaları tam olarak anlamak gerekmeden zengin dil hizmetleri sunabilir.

## <a name="how-work-on-the-lsp-started"></a>LSP üzerinde çalışma nasıl başlatılır

LSP zaman içinde gelişmiştir ve bugün sürüm 3,0 ' dir. C# için zengin düzen özellikleri sağlamak amacıyla bir dil sunucusu kavramı OmniSharp tarafından çekildiğinde başlatılır. İlk başta, OmniSharp HTTP protokolünü bir JSON yükünden kullandı ve [Visual Studio Code](https://code.visualstudio.com)gibi çeşitli düzenleyicilerle tümleşiktir.

Aynı zamanda, Microsoft, bir TypeScript dil sunucusunda çalışmaya başlamıştır ve Emacs ve alt açık metin gibi düzenleyicilerde TypeScript 'i destekleme fikrini sağlar. Bu uygulamada, bir düzenleyici, TypeScript sunucu işlemiyle STDIN/STDOUT üzerinden iletişim kurar ve istekler ve yanıtlar için V8 hata ayıklayıcı protokolü tarafından ilham bir JSON yükü kullanır. TypeScript sunucusu TypeScript alt lime eklentisine tümleştirildi ve zengin TypeScript düzenlemesi için VS Code.

İki farklı dil sunucusu tümleştirmeden sonra, VS Code ekibi düzenleyiciler ve Ides için ortak bir dil sunucusu protokolü keşfetmeye başladı. Ortak protokol, dil sağlayıcısının farklı Ides tarafından tüketilen tek bir dil sunucusu oluşturmasını sağlar. Bir dil sunucusu tüketicisi yalnızca protokolün istemci tarafını bir kez uygulamalıdır. Bu, hem dil sağlayıcısı hem de dil tüketicisi için bir Win-WIN durumuna neden olur.

Dil sunucusu protokolü, TypeScript sunucusu tarafından kullanılan protokolle başlatılır ve bu, VS Code dil API 'SI tarafından ilham daha fazla dil özellikleriyle genişletiliyor. Protokol, basitliği ve mevcut kitaplıkları nedeniyle uzaktan çağrı için JSON-RPC ile desteklenir.

VS Code takım prototipte, Lint (Scan) bir dosyaya yönelik isteklere yanıt veren ve algılanan bir uyarı ve hata kümesi döndüren birkaç Lint aracıdır dil sunucusu uygulayarak protokolü bir biçimde yazmış. Amaç, bir belgede Kullanıcı düzenlemeleri olduğu için bir dosyayı Lint idi. Bu, bir düzenleyici oturumu sırasında birçok farklı istek olacağı anlamına gelir. Her kullanıcı düzenlemesi için yeni bir oluşturma işleminin başlatılması gerekmemesi için bir sunucunun çalışır durumda tutulması ve çalışıyor olması mantıklıdır. VS Code eslint ve tslint uzantıları da dahil olmak üzere çeşitli Lint aracıdır sunucuları uygulandı. Bu iki Lint aracıdır sunucu her ikisi de TypeScript/JavaScript 'te ve Node.js üzerinde çalıştırılır. Bunlar, protokolün istemci ve sunucu bölümünü uygulayan bir kitaplığı paylaşır.

## <a name="how-the-lsp-works"></a>LSP 'nin nasıl çalıştığı

Bir dil sunucusu kendi sürecinde çalışır ve Visual Studio veya VS Code gibi araçlar, JSON-RPC üzerinden dil protokolünü kullanarak sunucuyla iletişim kurar. Özel bir işlemde çalışan dil sunucusunun başka bir avantajı, tek bir işlem modeliyle ilgili performans sorunlarının kaçınılmalarıdır. Gerçek aktarım kanalı, hem istemci hem de sunucu Node.js yazılmışsa, stdio, Sockets, adlandırılmış kanallar veya düğüm IPC olabilir.

Bir araç ve dil sunucusunun rutin bir düzenleyen oturumu sırasında nasıl iletişim kurduğu aşağıda verilmiştir:

![LSP akış diyagramı](media/lsp-flow-diagram.png)

* **Kullanıcı, araçta bir dosya (belge olarak adlandırılır) açar**: araç, dil sunucusuna bir belgenin açık olduğunu bildirir (' TextDocument/didOpen '). Bundan böyle açık olan belge hakkındaki gerçeği, artık dosya sisteminde değildir ancak bellekte araç tarafından tutulur.

* **Kullanıcı düzenleme yapar**: araç, sunucuya Belge değişikliği (' TextDocument/didChange ') hakkında bilgilendirir ve programın anlam bilgisi dil sunucusu tarafından güncelleştirilir. Bu durumda, dil sunucusu bu bilgileri analiz eder ve algılanan hatalar ve uyarılar (' textDocument/publishDiagnostics ') ile araca bildirir.

* **Kullanıcı Düzenleyicideki bir sembol üzerinde "tanıma git" i yürütür**: araç iki parametre ile bir ' textDocument/Definition ' isteği gönderir: (1) belge URI 'si ve (2) tanım Isteğinin sunucuya git olarak başlatıldığı metin konumu. Sunucu, belge URI 'SI ile yanıt verir ve sembolün tanımı belgenin içinde konumu.

* **Kullanıcı belgeyi kapatır (dosya)**: bir ' TextDocument/didClose ' bildirimi araçtan gönderilir. Bu, dil sunucusuna belgenin artık bellekte olmadığını ve geçerli içeriğin dosya sistemi üzerinde güncel olduğunu bildirerek gösterir.

Bu örnekte, protokolün "tanıma git", "tüm başvuruları bul" gibi düzenleyici özellikleri düzeyinde dil sunucusuyla nasıl iletişim kurduğu gösterilmektedir. Protokol tarafından kullanılan veri türleri, şu anda açık metin belgesi gibi düzenleyici veya IDE ' veri türleri ' ve imlecin konumunu kullanır. Veri türleri, genellikle soyut sözdizimi ağaçları ve derleyici sembolleri sağlayan bir programlama dili etki alanı modeli düzeyinde değildir (örneğin, çözümlenen türler, ad alanları,...). Bu, protokolü önemli ölçüde basitleştirir.

Şimdi ' textDocument/Definition ' isteğine daha ayrıntılı bir şekilde bakalım. Aşağıda, bir C++ belgesinde "tanıma git" isteğine yönelik istemci aracı ve dil sunucusu arasında gidip gelen yükleri verilmiştir.

Bu istek budur:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Bu yanıt:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Geriye dönük olarak, programlama dili modeli düzeyinde değil, veri türlerini düzenleyici düzeyinde açıklamak, dil sunucusu protokolünün başarısı için nedenlerinden biridir. Bir metin belgesi URI 'sini veya bir imleç konumunu, soyut bir sözdizimi ağacını ve farklı programlama dillerinde derleyici sembollerini standartlaştırarak standartlaştırmak çok daha basittir.

Kullanıcı farklı dillerde çalışırken, VS Code her bir programlama dili için genellikle bir dil sunucusu başlatır. Aşağıdaki örnekte, kullanıcının Java ve SASS dosyalarında çalıştığı bir oturum gösterilmektedir.

![Java ve Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Özellikler

Her dil sunucusu, protokol tarafından tanımlanan tüm özellikleri destekleyebilir. Bu nedenle, istemci ve sunucu, ' yetenekler ' aracılığıyla desteklenen özellik kümesini duyurur. Örnek olarak, bir sunucu ' textDocument/Definition ' isteğini işleyebileceğini duyurur, ancak ' çalışma alanı/sembol ' isteğini işleyemeyebilir. Benzer şekilde, istemciler bir belge kaydedilmeden önce ' bildirimleri kaydetmek üzere ' sunabiledikleri ve bir sunucunun düzenlenmiş belgeyi otomatik olarak biçimlendirmek için metinsel düzenlemeler oluşturabildiğini duyurur.

## <a name="integrating-a-language-server"></a>Bir dil sunucusunu tümleştirme

Bir dil sunucusunun belirli bir araçla gerçek tümleştirmesi dil sunucusu protokolü tarafından tanımlanmamıştır ve araç uygulayıcılar için bırakılır. Bazı araçlar, dil sunucularının her türlü dil sunucusu ile başlayabileceğini ve iletişim kurmasını sağlayan bir uzantıya sahip olarak, dil sunucularını genel bir şekilde tümleştirin. VS Code gibi diğerleri, dil sunucusu başına özel bir uzantı oluşturarak bir uzantının bazı özel dil özellikleri sağlayabilmesini sağlar.

Dil sunucularının ve istemcilerin uygulanmasını basitleştirmek için, istemci ve sunucu bölümlerinin kitaplıkları veya SDK 'Ları vardır. Bu kitaplıklar farklı diller için verilmiştir. Örneğin, bir dil sunucusunun bir VS Code uzantısına ve başka bir [dil sunucusu NPM modülüne](https://www.npmjs.com/package/vscode-languageserver) tümleştirilmesini kolaylaştırmak için bir dil [istemcisi npm modülü](https://www.npmjs.com/package/vscode-languageclient) , Node.js kullanarak bir dil sunucusu yazmak için kullanılır. Bu, destek kitaplıklarının geçerli [listesidir](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) .

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Visual Studio 'da dil sunucusu protokolünü kullanma

* [Dil sunucusu protokol uzantısı ekleme](adding-an-lsp-extension.md) -bir dil sunucusunu Visual Studio ile tümleştirme hakkında bilgi edinin.
