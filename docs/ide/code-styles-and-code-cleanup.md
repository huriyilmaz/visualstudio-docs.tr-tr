---
title: Kod stili seçenekleri ve kod temizleme
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9d540339ca25fc42fc05df4818a6d05204ccae0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301862"
---
# <a name="code-style-preferences"></a>Kod stili tercihleri

[EditorConfig dosyasını](#code-styles-in-editorconfig-files)kullanarak veya Visual Studio'da metin düzenleyicisi [ **Seçenekleri** sayfasında](#code-styles-in-the-options-dialog-box)düzenlediğiniz tüm kodlar için proje başına kod stili ayarlarını tanımlayabilirsiniz. C# kodu için Visual Studio'yu kod **temizleme** (Visual Studio 2019) ve Format **Belgesi** (Visual Studio 2017) komutlarını kullanarak bu kod stili tercihlerini uygulayacak şekilde yapılandırabilirsiniz.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'daki Düzenleyici davranışına](/visualstudio/mac/editor-behavior)bakın.

## <a name="code-styles-in-editorconfig-files"></a>EditorConfig dosyalarında kod stilleri

.NET için [kod stili ayarları,](../ide/editorconfig-code-style-settings-reference.md) projenize bir [EditorConfig](create-portable-custom-editor-options.md) dosyası eklenerek belirtilebilir. EditorConfig dosyaları Visual Studio kişiselleştirme hesabı yerine bir kod tabanı ile ilişkilidir. EditorConfig dosyasındaki ayarlar, **Seçenekler** iletişim kutusunda belirtilen kod stillerine göre önceliklidir. Repo'nuza veya projenize tüm katkıda bulunanlar için kodlama stilleri zorlamak istediğinizde bir EditorConfig dosyası kullanın.

::: moniker range=">=vs-2019"

EditorConfig dosyanızı el ile doldurabilir veya Visual Studio **Options** iletişim kutusunda seçtiğiniz kod stili ayarlarını temel alınca dosyayı otomatik olarak oluşturabilirsiniz. Bu seçenekler sayfası **Tools** > **Options** > **Metin Düzenleyicisi** > [**C#** veya **Temel**] > **Code Style** > **General'da**mevcuttur. Bu **Seçenekler** sayfasındaki ayarlara göre otomatik olarak bir kodlama stili *.editorconfig* dosyası oluşturmak için **ayarlardan .editorconfig dosyasını oluştur'u** tıklatın.

![Visual Studio 2019'daki ayarlardan editorconfig dosyası oluşturma](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Seçenekler iletişim kutusundaki kod stilleri

Kod stili **tercihleri, Araçlar** menüsünden **Seçenekler** iletişim kutusunu açarak tüm C# ve Visual Basic projeleriniz için ayarlanabilir. **Seçenekler** iletişim kutusunda, **Metin Düzenleyicisi** > [**C#** veya **Temel**] > Kod Stili**Genel'i** **Code Style** > seçin.

Listedeki her öğe, seçildiğinde tercihin önizlemesini gösterir:

::: moniker range="vs-2017"

![Kod stili seçenekleri](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Kod stili seçenekleri](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Bu pencerede ayarlanan seçenekler Visual Studio kişiselleştirme hesabınız için geçerlidir ve belirli bir proje veya kod tabanıyla ilişkili değildir. Buna ek olarak, sürekli tümleştirme (CI) oluşturur dahil olmak üzere, yapı zamanında zorlanmaz. Kod stili tercihlerini projenizle ilişkilendirmek ve yapı sırasında stillerin uygulanmasını istiyorsanız, projeyle ilişkili [bir .editorconfig dosyasında](#code-styles-in-editorconfig-files) tercihleri belirtin.

### <a name="preference-and-severity"></a>Tercih ve önem

Bu sayfadaki her kod stili ayarı için, her satırdaki açılır düşüşleri kullanarak **Tercih** ve **Önem Değerlerini** ayarlayabilirsiniz. Önem derecesi Yalnızca **ReFactoring**, **Öneri**, **Uyarı**veya **Hata**olarak ayarlanabilir. Bir kod stili için [Hızlı Eylemler'i](../ide/quick-actions.md) etkinleştirmek istiyorsanız, **Önem Derecesi** ayarını Yalnızca **Yeniden Düzenleme**dışında bir şey olarak ayarlandığından emin olun. **Hızlı Eylemler** ampul ![ampul](media/light-bulb-dropdown.png), hata ![ampul](media/error-bulb.png)hata ampul ![ampul](media/screwdriver.png) , veya tornavida tornavida simgesi tercih edilmeyen bir stil kullanıldığında görünür, ve otomatik olarak tercih edilen stil kod yeniden yazmak için **Hızlı Eylemler** listesinde bir seçenek seçebilirsiniz.

## <a name="apply-code-styles"></a>Kod stilleri uygulama

::: moniker range="vs-2017"

**Biçimbelge** komutunu **(Gelişmiş** > **Biçim Belgesini****Düzenle)** > kod stili ayarlarınızı (EditorConfig dosyasıveya **Kod Stili** seçeneklerinden) ve yaptığı normal biçimlendirmeyi (girintinasyon gibi) uygulamak üzere yapılandırabilirsiniz. Proje için bir *.editorconfig* dosyası varsa, bu ayarlar önceliklidir.

> [!NOTE]
> **Belge biçimlerini** kullanarak kod stilleri uygulamak yalnızca C# kod dosyaları için kullanılabilir. Bu deneysel bir özelliktir.

[Biçimlendirme seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings) **Biçimlendirme Belgesi'nin** hangi ayarların uygulanmasını istediğinizi yapılandırın.

![Visual Studio 2017'de biçim belgesi için kod stili ayarları](media/format-document-settings-experiment.png)

> [!TIP]
> **Hiçbiri** şiddetiyle yapılandırılan kurallar kod temizlemeye katılmaz, ancak Hızlı Eylemler **ve Yeniden Faktörler** menüsü üzerinden tek tek uygulanabilir.

**Belgebiçimlendirme** komutunu ilk kez tetiklediğiniz de, sarı bir bilgi çubuğu kod temizleme ayarlarınızı yapılandırmanızı ister.

::: moniker-end

::: moniker range=">=vs-2019"

C# kod dosyaları için Visual Studio 2019'da editörün alt kısmında bir **Code Cleanup** düğmesi bulunur (klavye: **Ctrl**+**K**, **Ctrl**+**E**) bir EditorConfig dosyasından veya **Kod Stili** seçenekleri sayfasından kod stilleri uygulamak için. Proje için bir *.editorconfig* dosyası varsa, bunlar öncelikli ayarlardır.

![Visual Studio 2019'da kod temizleme yi gerçekleştirin](media/execute-code-cleanup.png)

> [!TIP]
> **Hiçbiri** şiddetiyle yapılandırılan kurallar kod temizlemeye katılmaz, ancak Hızlı Eylemler **ve Yeniden Faktörler** menüsü üzerinden tek tek uygulanabilir.

İlk olarak, Yapılandırma Kodu Temizleme iletişim kutusunda hangi kod stillerini (iki profilden birinde) uygulamak istediğinizi **yapılandırın.** Bu iletişim kutusunu açmak için, kod temizleme süpürge simgesinin yanındaki genişletici okunu tıklatın ve ardından **Kod Temizlemeyi Yapıla'yı**seçin.

![Visual Studio 2019'da Kod Temizlemeyi Yapılandırma](media/configure-code-cleanup.png)

Kod temizlemeyi yapılandırıldıktan sonra, kod temizlemeyi çalıştırmak için süpürge simgesine tıklayabilir veya **Ctrl**+**K**, **Ctrl**+**E** tuşuna basabilirsiniz. Ayrıca tüm projeveya çözüm genelinde kod temizleme çalıştırabilirsiniz. **Çözüm Gezgini'nde**proje veya çözüm adına sağ tıklayın, **Analiz ve Kod Temizleme'yi**seçin ve ardından Kodu **Temizlemeyi Çalıştır'ı**seçin.

![Tüm proje veya çözümde Kod Temizleme'yi çalıştırma](media/run-code-cleanup-project-solution.png)

Bir dosyayı her kaydedişinizde kod stili ayarlarınızın uygulanmasını istiyorsanız, [Kaydet uzantısındaki Kod Temizleme'yi](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) beğenebilirsiniz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
- [EditorConfig için .NET kodlama kuralı ayarları](../ide/editorconfig-code-style-settings-reference.md)
- [Editör davranışı (Mac için Visual Studio)](/visualstudio/mac/editor-behavior)
