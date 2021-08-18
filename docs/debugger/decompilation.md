---
title: Hata ayıklarken .NET kodunu derlemeyi kaldırma | Microsoft Docs
description: Visual Studio 'de hata ayıklarken .NET derlemelerinden kaynak kodu oluşturun ve ekleyin. Gömülü kaynak kodu ayıklayın ve görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 2/2/2020
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 024d202122452c21594ed04dbf9c96256e73ca6f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112860"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Hata ayıklama sırasında .NET derlemelerinden kaynak kodu oluşturma

Bir .NET uygulamasında hata ayıklarken, sahip olmadığınız kaynak kodu görüntülemek istediğinizi fark edebilirsiniz. Örneğin, bir özel duruma bölme veya bir kaynak konuma gitmek için çağrı yığınını kullanma.

> [!NOTE]
> * Kaynak kodu oluşturma (ayrıştırılmış) yalnızca .NET uygulamalarında kullanılabilir ve açık kaynaklı [ılspy](https://github.com/icsharpcode/ILSpy) projesini temel alır.
> * decompilation yalnızca Visual Studio 2019 16,5 ve üzeri sürümlerde kullanılabilir.
> * [suppressildasmattribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) özniteliğini bir derlemeye veya modüle uygulamak, Visual Studio derlemeyi kaldırmaya engel olur.

## <a name="generate-source-code"></a>Kaynak kodu oluştur

hata ayıklarken ve kullanılabilir kaynak kodu olmadığında Visual Studio **kaynak bulunamadı** belgeyi gösterir veya derleme için semboller yoksa, **hiçbir sembol yüklenmedi** . Her iki belgede de geçerli konum için C# kodu üreten bir **derleme kaynak kodu** seçeneği vardır. Oluşturulan C# kodu, diğer tüm kaynak kodlarda olduğu gibi kullanılabilir. Kodu görüntüleyebilir, değişkenleri inceleyebilir, kesme noktalarını ayarlayabilir ve benzerlerini yapabilirsiniz.

### <a name="no-symbols-loaded"></a>Yüklü sembol yok

Aşağıdaki çizimde **hiçbir simge yüklenmedi** iletisi gösterilmektedir.

![Simge yüklü belge olmayan ekran görüntüsü](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Kaynak bulunamadı

Aşağıdaki çizimde **kaynak bulunamadı** iletisi gösterilmektedir.

![Kaynak bulunamadı belgesinin ekran görüntüsü](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Derleme için kaynakları oluşturma ve katıştırma

Belirli bir konum için kaynak kodu oluşturmaya ek olarak, belirli bir .NET derlemesi için tüm kaynak kodu oluşturabilirsiniz. Bunu yapmak için **modüller** penceresine ve bir .NET derlemesinin bağlam menüsünden gidin ve ardından **kaynak kodu derlemeyi kaldırma** komutunu seçin. Visual Studio, derleme için bir sembol dosyası oluşturur ve sonra kaynağı sembol dosyasına katıştırır. Sonraki bir adımda, gömülü kaynak kodu [ayıklayabilirsiniz](#extract-and-view-the-embedded-source-code) .

![Kaynak derlemeyi kaldırma komutuyla modüller penceresinde derleme bağlam menüsünün ekran görüntüsü.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Gömülü kaynak kodu ayıklama ve görüntüleme

**Modüller** penceresinin bağlam menüsündeki **kaynak kodu Ayıkla** komutunu kullanarak bir sembol dosyasına katıştırılmış kaynak dosyalarını ayıklayabilirsiniz.

![Kaynakları Ayıkla komutuyla modüller penceresinde derleme bağlam menüsünün ekran görüntüsü.](media/decompilation-extract-source-code.png)

Ayıklanan kaynak dosyalar çözüme [çeşitli dosyalar](../ide/reference/miscellaneous-files.md)olarak eklenir. Çeşitli Dosyalar özelliği, Visual Studio varsayılan olarak kapalıdır. Bu özelliği **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **belgeleri**  >  **Çözüm Gezgini onay kutusundaki çeşitli dosyaları göster ' de** etkinleştirebilirsiniz. Bu özelliği etkinleştirmeksizin ayıklanan kaynak kodunu açamazsınız.

![Çeşitli dosyalar seçeneğinin etkinleştirildiği araçlar seçenek sayfasının ekran görüntüsü.](media/decompilation-tools-options-misc-files.png)

Ayıklanan kaynak dosyaları **Çözüm Gezgini** içindeki çeşitli dosyalarda görüntülenir.

![Çeşitli dosyalarla Çözüm Gezgini 'nin ekran görüntüsü.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Bilinen sınırlamalar

### <a name="requires-break-mode"></a>Kesme modunu gerektirir

Ön derleme kullanarak kaynak kodu oluşturmak yalnızca hata ayıklayıcı kesme modundayken ve uygulama duraklatıldığında mümkündür. örneğin, Visual Studio kesme moduna bir kesme noktasına veya bir özel duruma girdiğinde girer. **tümünü kes** komutunu ( ![ tümünü kes simgesi) kullanarak kodunuzun çalışması için bir dahaki sefer Visual Studio kolayca tetikleyebilirsiniz ](media/decompilation-break-all.png) .

### <a name="decompilation-limitations"></a>Derlemeyi kaldırma sınırlamaları

.NET derlemelerinde kullanılan ara biçimden (IL) kaynak kodu oluşturma bazı ilgili sınırlamalara sahiptir. Bu nedenle, oluşturulan kaynak kodu özgün kaynak kodu gibi görünmüyor. Birçok fark, çalışma zamanında orijinal kaynak kodundaki bilgilerin gerekli olmadığı yerlerde yer vardır. Örneğin, boşluk, açıklamalar ve yerel değişkenlerin adları gibi bilgiler çalışma zamanında gerekli değildir. Programın, orijinal kaynak kodu yerine nasıl çalıştığını ve nasıl çalıştığını anlamak için oluşturulan kaynağı kullanmanızı öneririz.

### <a name="debug-optimized-or-release-assemblies"></a>İyileştirilmiş veya yayın derlemelerinde hata ayıkla

Derleyici iyileştirmeleri kullanılarak derlenen bir derlemeden derlenen kodda hata ayıklarken, aşağıdaki sorunlar boyunca karşılaşabilirsiniz:
- Kesme noktaları her zaman eşleşen kaynak konumunu bağlamayabilir.
- Adımlamayı her zaman doğru konuma ilerlemeyebilir.
- Yerel değişkenler doğru adlara sahip olamaz.
- Bazı değişkenler, değerlendirme için kullanılamayabilir.

GitHub sorunu: [ıkeskincode. decompiler ile VS hata ayıklayıcısına tümleştirme](https://github.com/icsharpcode/ILSpy/issues/1901)hakkında daha fazla ayrıntı bulunabilir.

### <a name="decompilation-reliability"></a>Derlemeyi kaldırma güvenilirliği

Bir dizi derleme girişiminin görece küçük bir yüzdesi hata oluşmasına neden olabilir. Bunun nedeni ılspy 'da dizi noktası null başvuru hatasıdır.  Bu sorunları ayırarak ve derleme girişimini sorunsuz bir şekilde başarısız hale getirerek hatayı hafifledik.

GitHub sorunu: [ıkeskincode. decompiler ile VS hata ayıklayıcısına tümleştirme](https://github.com/icsharpcode/ILSpy/issues/1901)hakkında daha fazla ayrıntı bulunabilir.

### <a name="limitations-with-async-code"></a>Zaman uyumsuz kodlu sınırlamalar

Zaman uyumsuz/await kod desenleriyle derlemeyi kaldırma modüllerinden sonuçlar tamamlanmamış veya tamamen başarısız olabilir. Zaman uyumsuz/await ve yield durumu-makinelerin ılspy uygulamasının yalnızca kısmen uygulanmış olması. 

GitHub sorunu: [PDB oluşturucu durumu](https://github.com/icsharpcode/ILSpy/issues/1422)' nda daha fazla ayrıntı bulunabilir.

### <a name="just-my-code"></a>Yalnızca Kendi Kodum

[Yalnızca kendi kodum (jmc)](./just-my-code.md) ayarları, Visual Studio sistem, çerçeve, kitaplık ve diğer kullanıcı olmayan çağrılar üzerinde ilerme olanağı sağlar. Bir hata ayıklama oturumu sırasında **modüller** penceresi, hata ayıklayıcının kodum (Kullanıcı kodu) olarak hangi kod modüllerine davranılması gerektiğini gösterir.

En iyileştirilmiş veya yayın modüllerinin derlenmesi Kullanıcı olmayan kod üretir. Hata ayıklayıcı, derlenmiş Kullanıcı olmayan kodunuzda kaparsa **kaynak** penceresi görünmez. Yalnızca kendi kodum devre dışı bırakmak için,   >  Genel hata ayıklama > Araçlar **Seçenekler** (veya **hata ayıklama**  >  **seçenekleri**) bölümüne gidin   >  ve **yalnızca kendi kodum etkinleştir** seçimini kaldırın.

### <a name="extracted-sources"></a>Ayıklanan kaynaklar

Derlemeden ayıklanan kaynak kodu aşağıdaki sınırlamalara sahiptir:
- Oluşturulan dosyaların adı ve konumu yapılandırılabilir değildir.
- Dosyalar geçicidir ve Visual Studio tarafından silinir.
- Dosyalar tek bir klasöre ve özgün kaynakların kullanılmayan tüm klasör hiyerarşisine yerleştirilir.
- Her bir dosyanın dosya adı, dosyanın sağlama toplamı karmasını içerir.

### <a name="generated-code-is-c-only"></a>Oluşturulan kod yalnızca C#
Decompilation yalnızca C# dilinde kaynak kodu dosyaları oluşturur. Başka herhangi bir dilde dosya oluşturma seçeneği yoktur.