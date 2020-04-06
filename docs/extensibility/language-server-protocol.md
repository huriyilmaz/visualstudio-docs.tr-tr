---
title: Language Server Protocol Genel Bakış | Microsoft Dokümanlar
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703108"
---
# <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

## <a name="what-is-the-language-server-protocol"></a>Dil Sunucusu Protokolü nedir?

Kaynak kodu otomatik tamamlama veya bir düzenleyici veya IDE bir programlama dili için **Tanımıgit** gibi zengin düzenleme özellikleri destekleyen geleneksel olarak çok zor ve zaman alıcıdır. Genellikle bir etki alanı modeli (tarayıcı, parser, bir tür denetleyicisi, bir oluşturucu ve daha fazlası) düzenleyici veya IDE programlama dilinde yazma gerektirir. Örneğin, Eclipse IDE'de C/C++ desteği sağlayan Eclipse CDT eklentisi Java'da yazılır, çünkü Eclipse IDE'nin kendisi Java'da yazılır. Bu yaklaşımı n ardından, Visual Studio Code için TypeScript'te bir C/C++ etki alanı modeli ve Visual Studio için C#'da ayrı bir etki alanı modeli uygulamak anlamına gelir.

Bir geliştirme aracı varolan dile özgü kitaplıkları yeniden kullanabiliyorsa, dile özgü etki alanı modelleri oluşturmak da çok daha kolaydır. Ancak, bu kitaplıklar genellikle programlama dilinin kendisinde uygulanır (örneğin, iyi C/C++ etki alanı modelleri C/C++'da uygulanır). C/C++ kitaplığını TypeScript'te yazılmış bir düzenleyiciye entegre etmek teknik olarak mümkündür, ancak bunu yapmak zordur.

### <a name="language-servers"></a>Dil sunucuları

Başka bir yaklaşım kendi sürecinde kütüphane çalıştırmak ve onunla konuşmak için süreçler arası iletişim kullanmaktır. İleri geri gönderilen iletiler bir protokol oluşturur. Dil sunucusu protokolü (LSP), geliştirme aracı ile dil sunucusu işlemi arasında değiş tokuş edilen iletileri standartlaştırmanın ürünüdür. Dil sunucuları veya iblisler kullanarak yeni veya yeni bir fikir değildir. Vim ve Emacs gibi editörler semantik otomatik tamamlama desteği sağlamak için bir süredir bunu yapıyor. LSP'nin amacı, bu tür tümleştirmeleri basitleştirmek ve dil özelliklerini çeşitli araçlara maruz bırakmak için yararlı bir çerçeve sağlamaktı.

Ortak bir protokole sahip olmak, dilin etki alanı modelinin varolan bir uygulamasını yeniden kullanarak programlama dili özelliklerinin en az yaygara yla bir geliştirme aracına tümleştirilmesine olanak tanır. Bir dil sunucusu arka ucu PHP, Python veya Java ile yazılabilir ve LSP çeşitli araçlara kolayca entegre edilebilir. Protokol, bir aracın temel etki alanı modeline özgü nüansları tam olarak anlamasına gerek kalmadan zengin dil hizmetleri sunabilmesi için ortak bir soyutlama düzeyinde çalışır.

## <a name="how-work-on-the-lsp-started"></a>LSP'deki çalışmalar nasıl başladı?

LSP zaman içinde gelişti ve bugün Sürüm 3.0'da. Bir dil sunucusu kavramı C # için zengin düzenleme özellikleri sağlamak için OmniSharp tarafından alındı başladı. Başlangıçta, OmniSharp bir JSON yükü ile HTTP protokolü kullanılan ve [Visual Studio Code](https://code.visualstudio.com)dahil olmak üzere çeşitli editörler entegre edilmiştir.

Aynı dönemde Microsoft, Emacs ve Sublime Text gibi editörlerde TypeScript'i destekleme fikriyle bir TypeScript dil sunucusu üzerinde çalışmaya başladı. Bu uygulamada, bir düzenleyici TypeScript sunucu işlemi ile stdin /stdout üzerinden iletişim kurar ve istek ler ve yanıtlar için V8 hata ayıklama protokolünden esinlenen bir JSON yükü kullanır. TypeScript sunucusu, zengin TypeScript düzenlemesi için TypeScript Sublime eklentisine ve VS Koduna entegre edilmiştir.

İki farklı dil sunucusunu entegre ettikten sonra, VS Code ekibi editörler ve IDA'lar için ortak bir dil sunucusu protokolü keşfetmeye başladı. Ortak bir iletişim kuralı, bir dil sağlayıcısının farklı IDA'lar tarafından tüketilebilen tek bir dil sunucusu oluşturmasına olanak tanır. Bir dil sunucusu tüketicisi protokolün istemci tarafını yalnızca bir kez uygulamak zorundadır. Bu, hem dil sağlayıcısı hem de dil tüketicisi için kazan-kazan durumu yla sonuçlanır.

Dil sunucusu protokolü TypeScript sunucusu tarafından kullanılan protokol ile başladı ve VS Code dil API'sinden esinlenerek daha fazla dil özelliğiyle genişletildi. Protokol, basitliği ve mevcut kitaplıkları nedeniyle uzaktan çağrı için JSON-RPC ile birlikte desteklidir.

VS Code ekibi, bir dosyayı tiftik (tarama) isteklerine yanıt veren ve algılanan uyarılar ve hatalar kümesini döndüren birkaç linter dil sunucusu uygulayarak protokolü prototiple prototiple tamamlar. Amaç, kullanıcı bir belgede editörlük sırasında çok sayıda linting isteği olacağı anlamına gelir, bir dosya yıkmak oldu. Her kullanıcı düzenlemesi için yeni bir linting işleminin başlatılmasıgerekmemesi için sunucuyu çalışır durumda tutmak mantıklıydı. VS Code'un ESLint ve TSLint uzantıları da dahil olmak üzere birçok linter sunucusu uygulandı. Bu iki linter sunucunun her ikisi de TypeScript/JavaScript'te uygulanır ve Düğüm.js'de çalıştırılır. Protokolün istemci ve sunucu bölümünü uygulayan bir kitaplığı paylaşırlar.

## <a name="how-the-lsp-works"></a>LSP nasıl çalışır?

Bir dil sunucusu kendi sürecinde çalışır ve Visual Studio veya VS Code gibi araçlar JSON-RPC üzerinden dil protokolünü kullanarak sunucuyla iletişim kurar. Özel bir işlemde çalışan dil sunucusunun bir diğer avantajı da, tek bir işlem modeliyle ilgili performans sorunlarının kaçınılmasıdır. Hem istemci hem de sunucu Düğüm.js olarak yazılmışsa, gerçek aktarım kanalı stdio, soketler, adlandırılmış borular veya düğüm ipc olabilir.

Aşağıda, bir aracın ve dil sunucusunun rutin düzenleme oturumu sırasında nasıl iletişim kurduğuna bir örnek verilmiştir:

![lsp akış diyagramı](media/lsp-flow-diagram.png)

* **Kullanıcı araçta bir dosya (belge olarak anılacaktır) açar**: Araç, dil sunucusuna belgenin açık olduğunu ('textDocument/didOpen') belirtir. Şu andan itibaren, belgenin içeriği hakkındaki gerçek artık dosya sisteminde değil, araç tarafından bellekte tutulur.

* **Kullanıcı düzenleme yapar**: Araç belge değişikliği ('textDocument/didChange') hakkında sunucuya bildirimde ve programın anlamsal bilgileri dil sunucusu tarafından güncelleştirilir. Bu durumda, dil sunucusu bu bilgileri analiz eder ve aracı algılanan hatalar ve uyarılarla ('textDocument/publishDiagnostics') ile bilgilendirir.

* **Kullanıcı, düzenleyicideki bir sembolüzerinde "Tanıma Git"i yürütür**: Araç iki parametreyle bir 'textDocument/definition' isteği gönderir: (1) URI belgesi ve (2) Tanıma Git isteğinin sunucuya başlatıldığı yerden metin konumu. Sunucu, URI belgesi ve sembolün tanımının belge içindeki konumuyla yanıt verir.

* **Kullanıcı belgeyi (dosyayı) kapatır**: Araçtan bir 'textDocument/didClose' bildirimi gönderilir ve dil sunucusuna belgenin artık bellekte olmadığını ve geçerli içeriğin artık dosya sisteminde güncel olduğunu bildirir.

Bu örnek, protokolün "Tanıya Git", "Tüm Başvuruları Bul" gibi düzenleyici özellikleri düzeyinde dil sunucusuyla nasıl iletişim kurduğunu göstermektedir. Protokol tarafından kullanılan veri türleri, şu anda açık olan metin belgesi ve imlecin konumu gibi düzenleyici veya IDE 'veri türleri'dir. Veri türleri genellikle soyut sözdizimi ağaçları ve derleyici sembolleri (örneğin, çözülmüş türleri, ad alanları, ...) sağlayacak bir programlama dili etki alanı modeli düzeyinde değildir. Bu, protokolü önemli ölçüde basitleştirir.

Şimdi 'textDocument/definition' isteğine daha ayrıntılı olarak bakalım. Aşağıda, C++ belgesindeki "Tanıma Git" isteği için istemci aracı ile dil sunucusu arasında giden yükler ve yükler verilmiştir.

Bu istek:

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

Geriye dönüp bakıldığında, program dili modeli düzeyinde değil, düzenleyici düzeyinde veri türleri açıklayan dil sunucusu protokolü başarı nedenlerinden biridir. Farklı programlama dilleri arasında soyut bir sözdizimi ağacı ve derleyici sembolleri standartlaştırma ile karşılaştırıldığında bir metin belgesi URI veya imleç konumunu standartlaştırmak çok daha kolaydır.

Bir kullanıcı farklı dillerde çalışıyorsa, VS Code genellikle her programlama dili için bir dil sunucusu başlatır. Aşağıdaki örnekte, kullanıcının Java ve SASS dosyaları üzerinde çalıştığı bir oturum gösterilmektedir.

![java ve sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Özellikler

Her dil sunucusu protokol tarafından tanımlanan tüm özellikleri destekleyebilir. Bu nedenle, istemci ve sunucu desteklenen özellik kümesini 'yetenekler' aracılığıyla duyurur. Örnek olarak, bir sunucu 'textDocument/definition' isteğini işleyebileceğini, ancak 'çalışma alanı/simgesi' isteğini işlemeyebileceğini bildirir. Benzer şekilde, istemciler bir belge kaydedilmeden önce 'kaydetmek üzere' bildirimleri sağlayabileceklerini, böylece bir sunucunun düzenlenen belgeyi otomatik olarak biçimlendirmek için metin düzenlemelerini hesaplayabildiğini bildirebilir.

## <a name="integrating-a-language-server"></a>Dil sunucusunun tümleştirilmesi

Bir dil sunucusunun belirli bir araca gerçek entegrasyonu, dil sunucusu protokolü tarafından tanımlanmaz ve araç uygulayıcılarına bırakılır. Bazı araçlar, her tür dil sunucusubaşlatıp konuşabilen bir uzantıya sahip olarak dil sunucularını genel olarak tümleştirir. VS Code gibi diğerleri, bir uzantın hala bazı özel dil özellikleri sağlamak mümkün böylece, dil sunucusu başına özel bir uzantısı oluşturun.

Dil sunucularının ve istemcilerin uygulanmasını kolaylaştırmak için istemci ve sunucu parçaları için kitaplıklar veya SDK'lar vardır. Bu kitaplıklar farklı diller için sağlanmaktadır. Örneğin, bir dil sunucusunun VS Kodu uzantısına entegrasyonunu kolaylaştırmak için bir [dil istemcisi npm modülü](https://www.npmjs.com/package/vscode-languageclient) ve Node.js kullanarak bir dil sunucusu yazmak için başka bir dil sunucusu [npm modülü](https://www.npmjs.com/package/vscode-languageserver) vardır. Bu, destek kitaplıklarının geçerli [listesidir.](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations)

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Visual Studio'da Dil Sunucusu Protokolü'nü Kullanma

* [Dil Sunucusu Protokolü uzantısı ekleme](adding-an-lsp-extension.md) - Bir dil sunucusunun Visual Studio'ya entegre edilmesi hakkında bilgi edinin.
