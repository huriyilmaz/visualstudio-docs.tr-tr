---
title: Dil Sunucusu Protokolüne Genel Bakış | Microsoft Docs
description: Dil sunucusu protokolünün dil özelliklerini çeşitli araçlara ifşa etmek için nasıl yararlı bir çerçeve sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 652164ec8553f0a332130d01f9c9d3a6d0537224
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152321"
---
# <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

## <a name="what-is-the-language-server-protocol"></a>Dil Sunucusu Protokolü nedir?

Düzenleyicide veya IDE'de programlama dili  için kaynak kodu otomatik tamamlamaları veya Tanıma Git gibi zengin düzenleme özelliklerini desteklemek geleneksel olarak oldukça zorlu ve zaman alan bir özelliktir. Genellikle düzenleyicinin veya IDE'nin programlama dilinde bir etki alanı modeli (tarayıcı, ayrıştırıcı, tür denetleyicisi, oluşturucu ve daha fazlası) yazmanız gerekir. Örneğin, Eclipse IDE'nin kendisi Java ile yazıldığı için Eclipse IDE'de C/C++ desteği sağlayan Eclipse CDT eklentisi Java'da yazılır. Bu yaklaşımın ardından, Visual Studio Code için TypeScript'te bir C/C++ etki alanı modeli ve Visual Studio için C# içinde ayrı bir etki alanı modeli uygulanması anlamına Visual Studio.

Bir geliştirme aracı mevcut dile özgü kitaplıkları yeniden kullanabilirse dile özgü etki alanı modelleri oluşturmak da çok daha kolaydır. Ancak, bu kitaplıklar genellikle programlama dilinin kendisinde uygulanır (örneğin, iyi C/C++ etki alanı modelleri C/C++ içinde uygulanır). C/C++ kitaplığını TypeScript'te yazılmış bir düzenleyiciyle tümleştirme teknik olarak mümkündür ancak bunu yapmak zordur.

### <a name="language-servers"></a>Dil sunucuları

Bir diğer yaklaşım da kitaplığı kendi işlemi içinde çalıştırmak ve işlemler arası iletişimi kullanarak bu kitaplıkla konuşmaktır. Geri ve ileri gönderilen iletiler bir protokol sağlar. Dil sunucusu protokolü (LSP), bir geliştirme aracı ile dil sunucusu işlemi arasında ileti alışverişi yapılan iletileri standart hale getirerek bir üründür. Dil sunucularını veya biraları kullanmak yeni veya yeni bir fikir değildir. Vim ve Emacs gibi düzenleyiciler bunu bir süredir semantik otomatik tamamlama desteği sağlamak için yapıyor. LSP'nin amacı bu tür tümleştirmeleri basitleştirmek ve dil özelliklerini çeşitli araçlara sunmak için kullanışlı bir çerçeve sağlamaktır.

Ortak bir protokole sahip olmak, dilin etki alanı modelinin mevcut bir uygulamasını yeniden kullanarak programlama dili özelliklerinin en az hatayla bir geliştirme aracıyla tümleşmesine olanak sağlar. Dil sunucusu arka uç PHP, Python veya Java ile yazabilir ve LSP bunu çeşitli araçlarla kolayca tümleştirebilirsiniz. Protokol, temel alınan etki alanı modeline özgü nüansları tam olarak anlamak zorunda kalmadan bir aracın zengin dil hizmetleri sunarak ortak bir soyutlama düzeyinde çalışır.

## <a name="how-work-on-the-lsp-started"></a>LSP'de çalışma nasıl başlatıldı

LSP zamanla gelişti ve bugün Sürüm 3.0'da. Bu, C# için zengin düzenleme özellikleri sağlamak için OmniSharp tarafından bir dil sunucusu kavramı top olduğunda başladı. OmniSharp başlangıçta BIR JSON yüküyle HTTP protokolünü kullandı ve bu protokol, ile birlikte çeşitli düzenleyicilerle [Visual Studio Code.](https://code.visualstudio.com)

Aynı zamanda Microsoft, Emacs ve Sublime Text gibi düzenleyicilerde TypeScript'i destekleme fikriyle bir TypeScript dil sunucusunda çalışmaya başlamıştır. Bu uygulamada, bir düzenleyici stdin/stdout aracılığıyla TypeScript sunucu işlemiyle iletişim kurar ve istekler ve yanıtlar için V8 hata ayıklayıcısı protokolünden esinlenen bir JSON yükü kullanır. TypeScript sunucusu, TypeScript Alt Eklentisi eklentisiyle tümleştirilmiştir ve zengin TypeScript VS Code için kullanılabilir.

İki farklı dil sunucusunu tümleştirdikten sonra, VS Code ekibi düzenleyiciler ve IDE'ler için ortak bir dil sunucusu protokolünü keşfetmeye başladı. Ortak bir protokol, dil sağlayıcısının farklı IDE'ler tarafından tüketilebilir tek bir dil sunucusu oluşturması sağlar. Dil sunucusu tüketicisi, protokolün istemci tarafını yalnızca bir kez uygulamalı. Bu, hem dil sağlayıcısı hem de dil tüketicisi için kazanma durumuna neden olur.

Dil sunucusu protokolü, TypeScript sunucusu tarafından kullanılan protokolle başladı ve dil API'sini kullanarak daha fazla dil VS Code genişletildi. Protokol, basitliği ve mevcut kitaplıkları nedeniyle uzaktan çağrı için JSON-RPC ile birlikte de kullanılabilir.

VS Code ekibi, bir dosyaya lint (tarama) isteklerine yanıt veren ve algılanan uyarı ve hatalardan oluşan bir kümeyi geri veren birkaç lint dili sunucusu kullanarak protokolün prototipini yaptı. Amaç, kullanıcı bir belgede düzenlemesi sırasında bir dosyaya lint yapmaktı. Bu da düzenleyici oturumu sırasında çok sayıda lint isteği olacağını gösterir. Her kullanıcı düzenlemesi için yeni bir linting işleminin başlatılamay için sunucunun açık ve çalışıyor olması mantıklıdır. VS Code'nin ESLint ve TSLint uzantıları dahil olmak üzere çeşitli linter sunucuları uygulanmıştır. Bu iki linter sunucusu, TypeScript/JavaScript'te uygulanır ve Node.js. Protokolün istemci ve sunucu bölümünü uygulayan bir kitaplığı paylaşırlar.

## <a name="how-the-lsp-works"></a>LSP nasıl çalışır?

Bir dil sunucusu kendi işlemi içinde çalışır ve JSON-RPC Visual Studio VS Code protokolünü kullanarak sunucuyla iletişim kurmak için VS Code gibi araçlar. Ayrılmış bir işlemde çalışan dil sunucusunun bir diğer avantajı, tek bir işlem modeliyle ilgili performans sorunlarının önüne geçılmasıdır. Gerçek aktarım kanalı stdio, yuvalar, adlandırılmış kanallar veya hem istemci hem de sunucu aynı anda yazılmışsa düğüm ipc Node.js.

Aşağıda, bir aracın ve dil sunucusunun rutin bir düzenleme oturumu sırasında nasıl iletişim kurarak iletişim kurması için bir örnek verilmiştir:

![lsp akış diyagramı](media/lsp-flow-diagram.png)

* **Kullanıcı aracında bir** dosya (belge olarak adlandırılır) açar: Araç, dil sunucusuna bir belgenin açık olduğunu ('textDocument/didOpen') belirtir. Bundan sonra belgenin içeriği hakkındaki gerçek artık dosya sisteminde değil, araç tarafından bellekte tutulmaktadır.

* **Kullanıcı düzenlemeler yapar:** Araç, belge değişikliği ('textDocument/didChange') hakkında sunucuya bilgi verir ve programın semantik bilgileri dil sunucusu tarafından güncelleştirilir. Bu durumda dil sunucusu bu bilgileri analiz eder ve algılanan hatalar ve uyarılar ('textDocument/publishDiagnostics') ile aracı bilgi verir.

* Kullanıcı düzenleyicide bir sembolde **"Tanıma Git"** ifadesini yürütür: Araç, iki parametreyle bir 'textDocument/definition' isteği gönderir: (1) belge URI'si ve (2) Tanıma Git isteğinin başlatıldığı metin konumu. Sunucu belge URI'si ve sembol tanımının belgenin içindeki konumuyla yanıt verir.

* **Kullanıcı belgeyi (dosya)** kapatır: Araçtan bir 'textDocument/didClose' bildirimi göndererek dil sunucusuna belgenin artık bellekte olmadığını ve geçerli içeriğin dosya sisteminde güncel olduğunu bildirmektedir.

Bu örnek, protokolün dil sunucusuyla "Tanıma Git", "Tüm Başvuruları Bul" gibi düzenleyici özellikleri düzeyinde nasıl iletişim kurarak iletişim kurarak nasıl iletişim kura olduğunu gösterir. Protokol tarafından kullanılan veri türleri düzenleyici veya şu anda açık olan metin belgesi ve imlecin konumu gibi IDE 'veri türleri'dir. Veri türleri genellikle soyut söz dizimi ağaçları ve derleyici sembolleri (çözümlenmiş türler, ad alanları, ...) sağlayacak programlama dili etki alanı modeli düzeyinde değildir. Bu, protokolü önemli ölçüde basitleştirmektedir.

Şimdi 'textDocument/definition' isteğine daha ayrıntılı bir şekilde bakalım. Aşağıda, bir C++ belgesinde "Tanıma Git" isteği için istemci aracı ile dil sunucusu arasında gidip gelen yükler verilmiştir.

İstek şu şekildedir:

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

Yanıt şu şekildedir:

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

Geçmişe dönük olarak, veri türlerini programlama dili modeli düzeyinde değil düzenleyici düzeyinde açıklama, dil sunucusu protokolünün başarısının nedenlerinden birisidir. Bir metin belgesi URI'sini veya imleç konumunu standart hale getirmek, soyut söz dizimi ağacını ve derleyici sembollerini farklı programlama dillerinde standart hale getirmekle karşılaştırıldığında çok daha kolaydır.

Bir kullanıcı farklı dillerle çalışırken, VS Code genellikle her programlama dili için bir dil sunucusu başlatır. Aşağıdaki örnekte kullanıcının Java ve SASS dosyaları üzerinde çalıştığını gösteren bir oturum gösterilmiştir.

![java ve sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Özellikler

Her dil sunucusu protokol tarafından tanımlanan tüm özellikleri desteklemez. Bu nedenle, istemci ve sunucu 'özellikler' aracılığıyla desteklenen özellik kümelerini duyurur. Örneğin, bir sunucu 'textDocument/definition' isteğini işleyene kadar bunu duyursa da 'çalışma alanı/sembol' isteğini işlemeyebilir. Benzer şekilde, bir sunucu düzenlenen belgeyi otomatik olarak biçimlendirmek için metinsel düzenlemeleri hesaplayacak şekilde, bir belgeyi kaydetmeden önce "kaydetmek üzere" bildirimleri sağlayabileceklerini duyurur.

## <a name="integrating-a-language-server"></a>Dil sunucusunu tümleştirme

Dil sunucusunun belirli bir araçla gerçek tümleştirmesi dil sunucusu protokolü tarafından tanımlanmaz ve araç uygulayıcılarına bıraktır. Bazı araçlar, dil sunucularını herhangi bir dil sunucusu türüyle başlatan ve konuşan bir uzantıya sahip olarak genel olarak tümleştirin. Bir uzantının VS Code sağlayabilecek şekilde dil sunucusu başına özel bir uzantı oluşturması gibi diğer bazı özellikler de vardır.

Dil sunucularının ve istemcilerin uygulanmasını basitleştirmek için, istemci ve sunucu parçaları için kitaplıklar veya SDK'lar vardır. Bu kitaplıklar farklı diller için sağlanır. Örneğin, bir dil sunucusunun bir VS Code uzantısıyla tümleşmesini kolaylaştıran bir dil istemcisi [npm](https://www.npmjs.com/package/vscode-languageclient) modülü ve bir dil sunucusu yazmak için başka bir dil sunucusu [npm](https://www.npmjs.com/package/vscode-languageserver) modülü Node.js. Bu, destek [kitaplıklarının](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) geçerli listesidir.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Visual Studio'da Dil Sunucusu Protokolünü kullanma

* [Dil Sunucusu Protokolü uzantısı ekleme](adding-an-lsp-extension.md) - Dil sunucusunu bir dil sunucusuyla tümleştirmeyi Visual Studio.
