---
title: Kod stili seçenekleri ve kod Temizleme
description: kod temizleme (Visual Studio 2019) ve biçim belgesi (Visual Studio 2017) komutlarını kullanarak kod stili tercihlerini uygulamaya Visual Studio nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 6d6f31d876516700307881135eca3b23eba26d687d6468142440078d98e48099
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358212"
---
# <a name="code-style-preferences"></a>Kod stili tercihleri

bir [editorconfig dosyası](#code-styles-in-editorconfig-files)kullanarak proje başına kod stili ayarları tanımlayabilir veya metin düzenleyici [ **seçenekleri** sayfasında](#code-styles-in-the-options-dialog-box)Visual Studio ' de düzenlediğiniz tüm kodlar için. C# kodu için, **kod temizleme** (Visual Studio 2019) ve **biçim belgesi** (Visual Studio 2017) komutlarını kullanarak bu kod stili tercihlerini uygulamak üzere Visual Studio de yapılandırabilirsiniz.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için [Mac için Visual Studio içindeki düzenleyici davranışı](/visualstudio/mac/editor-behavior)bölümüne bakın.

## <a name="code-styles-in-editorconfig-files"></a>EditorConfig dosyalarındaki kod stilleri

.NET için [kod stili ayarları](/dotnet/fundamentals/code-analysis/code-style-rule-options) , projenize bir [editorconfig](create-portable-custom-editor-options.md) dosyası eklenerek belirtilebilir. editorconfig dosyaları Visual Studio kişiselleştirme hesabı yerine bir kod temeli ile ilişkilendirilir. bir editorconfig dosyasındaki Ayarlar, **seçenekler** iletişim kutusunda belirtilen kod stillerinden önceliklidir. Deponuzda veya projenizde tüm katkıda bulunanlar için kodlama stillerini zorlamak istediğinizde bir EditorConfig dosyası kullanın.

::: moniker range=">=vs-2019"

editorconfig dosyanızı el ile doldurabilir veya Visual Studio **seçenekleri** iletişim kutusunda seçtiğiniz kod stili ayarlarını temel alarak dosyayı otomatik olarak oluşturabilirsiniz. Bu seçenekler sayfası **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi** > [**C#** veya **Basic**] > **kod stili**  >  **genel**' de bulunur. Bu **Seçenekler** sayfasındaki ayarlara göre otomatik olarak bir kodlama stili *. editorconfig* dosyası oluşturmak için, **ayarlardan. editorconfig dosyası oluştur** ' a tıklayın.

![Visual Studio 2019 ' deki ayarlardan editorconfig dosyası üret](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Seçenekler iletişim kutusundaki kod stilleri

kod stili tercihleri, **araçlar** menüsünden **seçenekler** iletişim kutusunu açarak tüm C# ve Visual Basic projeleriniz için ayarlanabilir. **Seçenekler** iletişim kutusunda, **metin Düzenleyicisi** > [**C#** veya **temel**] > **kod stili**  >  **genel**' i seçin.

Listedeki her bir öğe, seçildiğinde tercih listesinin bir önizlemesini gösterir:

::: moniker range="vs-2017"

![Kod stili seçenekleri](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Kod stili seçenekleri](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

bu pencerede ayarlanan seçenekler, Visual Studio kişiselleştirme hesabınıza uygulanabilir ve belirli bir proje veya kod temeli ile ilişkilendirilmemiş. Ayrıca, sürekli tümleştirme (CI) yapıları dahil olmak üzere derleme zamanında zorlanmaz. Kod stili tercihlerini projenizle ilişkilendirmek ve derleme sırasında uygulanan stilleri sağlamak istiyorsanız, tercihleri projeyle ilişkili bir [. editorconfig dosyasında](#code-styles-in-editorconfig-files) belirtin.

### <a name="preference-and-severity"></a>Tercih ve önem derecesi

Bu sayfadaki her kod stili ayarı için, her satırdaki açılan listeleri kullanarak **tercih** ve **önem derecesi** değerlerini ayarlayabilirsiniz. Önem derecesi **yalnızca yeniden düzenleme**, **öneri**, **Uyarı** veya **hata** olarak ayarlanabilir. Bir kod stili için [hızlı eylemleri](../ide/quick-actions.md) etkinleştirmek Istiyorsanız, **önem derecesi** ayarının **yalnızca yeniden düzenleme** dışında bir değere ayarlandığından emin olun.  :::image type="icon" source="media/light-bulb-dropdown.png"::: Tercih edilmeyen bir stil kullanıldığında ve hızlı eylemler açık ampul, hata ampul :::image type="icon" source="media/error-bulb.png"::: veya screwsürücü :::image type="icon" source="media/screwdriver.png"::: simgesi görünür ve kodu tercih edilen stile otomatik olarak yeniden yazmak için **hızlı eylemler** listesinde bir seçenek belirleyebilirsiniz.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Derlemede kod stilleri zorla

.net 5,0 RC2 SDK 'sını içeren Visual Studio 2019 sürüm 16,8 ' den başlayarak tüm .net projeleri için [derleme üzerinde .net kodlama kurallarını](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) uygulayabilirsiniz. Derleme zamanında, .NET kod stili ihlalleri uyarı veya "IDE" ön eki ile hatalar olarak görünür. Bu, kod tabanınızda tutarlı kod stillerini kesinlikle zorlamanıza olanak sağlar.

::: moniker-end

## <a name="apply-code-styles"></a>Kod stillerini Uygula

::: moniker range="vs-2017"

   >    >  Kod stili ayarlarınızı (bir editorconfig dosyası veya **kod stili** seçenekleri), yaptığı normal biçimlendirme (girintileme gibi) ile birlikte uygulamak için, biçim belgesi komutunu (Gelişmiş **Biçim belgesini** Düzenle) yapılandırabilirsiniz. Proje için bir *. editorconfig* dosyası varsa, bu ayarlar öncelik kazanır.

> [!NOTE]
> **Belgeyi Biçimlendir** komutunu kullanarak kod stillerini uygulamak yalnızca C# kod dosyaları için kullanılabilir. Bu bir deneysel özelliktir.

[Biçimlendirme seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings) **Belge biçimini biçimlendirmek** istediğiniz ayarları yapılandırın.

![Visual Studio 2017 belgesinde biçim belgesi için kod stili ayarları](media/format-document-settings-experiment.png)

> [!TIP]
> **Hiçbiri** önem derecesine sahip bir şekilde yapılandırılan kurallar kod temizlemesine katılmaz, ancak **Hızlı Eylemler ve yeniden düzenlemeler** menüsüyle tek tek uygulanabilir.

**Biçim belgesi** komutunu ilk kez tetikleyişinizde, sarı bir bilgi çubuğu kod temizleme ayarlarınızı yapılandırmanızı ister.

::: moniker-end

::: moniker range=">=vs-2019"

C# kod dosyaları için Visual Studio 2019, düzenleyicinin alt kısmındaki bir **kod temizleme** düğmesine sahiptir (klavye: **ctrl** + **K**, **ctrl** + **E**). bir editorconfig dosyasından veya **kod stili** seçenekleri sayfasından kod stilleri uygulamak için. Proje için bir *. editorconfig* dosyası varsa, bu ayarlar öncelik kazanır.

![Visual Studio 2019 ' de kod temizlemeyi yürütme](media/execute-code-cleanup.png)

> [!TIP]
> **Hiçbiri** önem derecesine sahip bir şekilde yapılandırılan kurallar kod temizlemesine katılmaz, ancak **Hızlı Eylemler ve yeniden düzenlemeler** menüsüyle tek tek uygulanabilir.

İlk olarak, **kod temizlemeyi Yapılandır** iletişim kutusunda hangi kod stillerini uygulamak istediğinizi (iki profilden birinde) yapılandırın. Bu iletişim kutusunu açmak için, kod temizleme Brob simgesinin yanındaki genişletici okuna ve ardından **kod temizlemeyi Yapılandır**' ı seçin.

![Visual Studio 2019 ' de kod temizlemeyi yapılandırma](media/configure-code-cleanup.png)

Kod temizlemeyi yapılandırdıktan sonra,  + kod temizlemeyi çalıştırmak için Broom simgesine tıklayabilir veya CTRL **K**, **CTRL** + **E** tuşlarına basabilirsiniz. Ayrıca, tüm proje veya çözümünüz genelinde kod temizleme işlemini de çalıştırabilirsiniz. **Çözüm Gezgini**' de proje veya çözüm adına sağ tıklayın, **Çözümle ve kod temizleme**' yi seçin ve ardından **kod temizlemeyi Çalıştır**' ı seçin.

![Kod temizlemeyi tüm proje veya çözüm genelinde Çalıştır](media/run-code-cleanup-project-solution.png)

Kod stili ayarlarınızın bir dosyayı her kaydedişinizde uygulanmasını istiyorsanız, [kayıt uzantısında kod temizlemeyi](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) beğenmeyebilirsiniz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
- [EditorConfig için .NET kodlama kuralı ayarları](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [düzenleyici davranışı (Mac için Visual Studio)](/visualstudio/mac/editor-behavior)
