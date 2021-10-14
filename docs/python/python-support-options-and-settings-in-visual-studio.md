---
title: Python için seçenekler ve ayarlar
description: Python kodu ve projeleriyle ilgili Visual Studio ayarları için başvuru.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 17cd4402fcf7f2dc3735a6c1776b91f67b6bd28d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968390"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio'da Python seçenekleri

Python seçeneklerini görüntülemek için Araçlar Seçenekler **menü komutunu** kullanın, Tüm ayarları göster'in seçili olduğundan emin olun ve  >   python'a **gidin:** 

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

Metin Düzenleyici Python Gelişmiş sekmesinde ve Metin Düzenleyici grubunun Ortam Yazı Tipleri ve Renkler sekmesinde Python'a özgü ek seçenekler  >    >     >   **de** vardır.

> [!Note]
> Deneysel **grubu,** hala geliştirme aşamasında olan ve burada belgelenmiş olan özellikler için seçenekler içerir. Bunlar genellikle Microsoft blog'larında [Python mühendisliği gönderileri içinde ele alınmıştır.](https://devblogs.microsoft.com/python/)

## <a name="general-options"></a>Genel seçenekler

(**Araçlar**  >  **Seçenekler**  >  **Python** sekmesi.)

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Sanal ortamlar Çıkış Penceresi çalışma zamanlarını gösterme**| Açık | Çıkış penceresinin **görünmesini** önlemek için temiz. |
| **Paketleri yüklerken Çıkış Penceresi kaldırmayı gösterir** | Açık | Çıkış penceresinin **görünmesini** önlemek için temiz. |
| **Ortam oluşturmak için bildirim çubuğunu gösterme** | Açık | *Visual Studio 2019'da.* Bu seçenek ayar olduğunda ve *kullanıcırequirements.txt* veya *environment.yml* dosyası içeren bir proje açtığında, Visual Studio varsayılan genel ortamı kullanmak yerine sırasıyla sanal ortam veya conda ortamı oluşturma önerilerini içeren bir bilgi çubuğu görüntüler. |
| **Paketleri yüklemek için bildirim çubuğunu gösterme** | Açık | *Visual Studio 2019'da.* Bu seçenek ayarlandığında ve *kullanıcı birrequirements.txt* dosyası içeren bir proje açtığında (ve varsayılan genel ortamı kullanmaz) Visual Studio bu gereksinimleri geçerli ortamda yüklü paketlerle karşılaştırıldığında. Herhangi bir paket eksikse Visual Studio yüklemek için bir istem görüntüler. |
| **Paket yöneticilerini her zaman yönetici olarak çalıştırma** | Kapalı | Tüm ortamlar `pip install` için her zaman ve benzer paket yöneticisi işlemlerini yükselter. Paketleri yüklerken, Visual Studio *c:\Program Files* gibi dosya sisteminin korumalı bir alanında bulunuyorsa yönetici ayrıcalıkları istenir. Bu istemde yalnızca bir ortam için yükleme komutunu her zaman yükseltmeyi seçebilirsiniz. Bkz. [Paketler sekmesi.](python-environments-window-tab-reference.md#packages-tab) |
| **İlk kullanım sırasında tamamlama db'lerini otomatik olarak oluşturma** | Açık | *IntelliSense Visual Studio 2017 sürüm 15.5 ve önceki sürümler ve sonraki sürümler için geçerlidir.* Bunu kullanan kod yazarak bir kitaplık için veritabanının tamamlanmasını öncelik sırasına alır. Daha fazla bilgi için [bkz. Intellisense sekmesi.](python-environments-window-tab-reference.md?view=vs-2017&preserve-view=true#intellisense-tab) |
| **Sistem genelindeKI PYTHONPATH değişkenlerini yoksayma** | Açık | PythonPATH varsayılan olarak yoksayılır çünkü Visual Studio ortamlarda ve projelerde arama yollarını belirtmek için daha doğrudan bir yol sağlar. Ayrıntılar [için bkz.](search-paths.md) Yolları arama. |
| **Bağlantılı dosya eklerken arama yollarını güncelleştirme** | Açık | Ayarlandıktan sonra, [](managing-python-projects-in-visual-studio.md#linked-files) IntelliSense'in [](search-paths.md) tamamlanma veritabanına bağlı dosya klasörünün içeriğini ekleyemediklerine göre bir projeye bağlı dosya eklemek Arama yolları'nın güncelleştirmelerini sağlar. Bu tür içerikleri tamamlama veritabanından dışlamak için bu seçeneği silin. |
| **İçe aktarılan modül bulunamazsa uyar** | Açık | İçe aktarılan bir modülün mevcut olmadığını ancak kod işlemi başka bir şekilde etkilemeyeceğini biliyorsanız uyarıları gizlemeye yönelik bu seçeneği silin. |
| **Tutarsız girintiyi olarak bildirme** | **Uyarılar** | Python yorumlayıcı kapsamı belirlemek için düzgün girintilemeye büyük ölçüde bağlı olduğundan, Visual Studio kodlama hatalarını belirtecek tutarsız girintiler algılayan uyarılar görüntüler. Hatalar daha **katı** olacak şekilde ayarlanmıştır ve bu da bu gibi durumlarda programın çıkışa neden olmasına neden olur. Bu davranışı tamamen devre dışı bırakmak için **Değil'i seçin.** |
| **Anketleri/haberleri denetleme** | **Haftada bir** | *Visual Studio 2017 ve önceki sürümler.* Python ile ilgili anketler ve Visual Studio içeren bir web sayfası içeren bir pencere açmasına izin verme sıklığı (varsa) ayarlar. Seçenekler Hiçbir **Zaman,** **Günde bir kez,** **Haftada bir ve** Ayda bir **seçeneğidir.** |
| **Kalıcı olarak gizlenen tüm iletişim kutularını sıfırla** düğmesi | yok | Farklı iletişim kutuları, Bunu **bir daha gösterme gibi seçenekler sağlar.** Bu seçenekleri temizlemek ve iletişim kutularının yeniden görüntüye neden olmak için bu düğmeyi kullanın. |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda seçenekleri

(**Araçlar** > **Seçenekler** > **Python** > **Conda** sekmesi.)

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Conda yürütülebilir yolu** | (boş) | Python iş yüküne *dahil edilen varsayılan* Miniconda yüklemesine güvenmek yerineconda.exeyürütülebilir dosyasının tam yolunu belirtir. Burada başka bir yol veriliyorsa, varsayılan yüklemeden ve kayıt defterinde belirtilen diğer conda.exe yürütülebilir dosyalardan önceliklidir. Anaconda veya Miniconda'nın daha yeni bir sürümünü el ile yükleyseniz veya varsayılan 64 bit dağıtım yerine 32 bit distro kullanmak istemeniz bu ayarı değiştirebilirsiniz. |

![Python seçeneklerinde Conda'nın seçili olduğu Visual Studio Araçları Seçenekleri iletişim kutusunun ve sağ bölmede gösterilen Conda yürütülebilir yol alanı ekran görüntüsü.](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Hata ayıklama seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Python**  >  **Hata ayıklama** sekmesi.)

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Hatalar olduğunda çalıştırmadan önce istem** | Açık | Ayar olduğunda, hataları içeren kodu çalıştırmak istediğinizden onay ister. Uyarıyı devre dışı bırakmak için bu seçeneğin temizlerini kullanın. |
| **İşlem anormal bir şekilde çıkışa geldiğinde girişi bekleyin**<br/><br/>**İşlem normal şekilde çıkışa geldiğinde girişi bekleyin** | On (her ikisi için) | Bir Python programı Visual Studio kendi konsol penceresinde çalışır. Varsayılan olarak pencere, programın çıkışından bağımsız olarak kapatmadan önce bir tuşa basmanız için bekler. Bu istemi kaldırmak ve pencereyi otomatik olarak kapatmak için bu seçeneklerden birini veya her ikisini de silin. |
| **Program çıktısını Hata Ayıklama Çıktı penceresine ayıklama** | Açık | Program çıkışını hem ayrı bir konsol penceresinde hem de Visual Studio **penceresinde** görüntüler. Çıkışı yalnızca ayrı konsol penceresinde göstermek için bu seçeneğin temizleme. |
| **Çıkış kodu sıfır olan SystemExit özel durumuyla kesme** | Kapalı | Ayarlanırsa, bu özel durumda hata ayıklayıcıyı durdurur. Temiz olduğunda hata ayıklayıcısı hata ayıklayıcıdan hatasız olarak çıkar. |
| **Python standart kitaplığında hata ayıklamayı etkinleştirme** | Kapalı | Hata ayıklama sırasında standart kitaplık kaynak koduna adımlamayı mümkün hale getirse de, hata ayıklayıcının başlaması için gereken süre artar.|
| **İşlev dönüş değerini göster** | Açık | *Visual Studio 2019'da.* Yereller penceresinde işlev dönüş **değerlerini görüntüler** ve ardından hata ayıklayıcısında işlev çağrısının üzerine adımlama (F10) |
| **Eski hata ayıklayıcısını kullanma** | Kapalı | *Visual Studio 2019'da.* Bu Visual Studio eski hata ayıklayıcısını kullanmalarını sağlar. Daha fazla bilgi için [bkz. Hata Ayıklama - Eski hata ayıklayıcısını kullanma.](debugging-python-in-visual-studio.md#use-the-legacy-debugger) |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Hata ayıklama sekmesi](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Hata ayıklama sekmesi](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Tanılama seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Python**  >  **Tanılama sekmesi.)**

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Analiz günlüklerini dahil edin** | Açık | Tanılamayı bir dosyaya kaydederken veya düğmeleri kullanarak panoya kopyalarken yüklü Python ortamlarının analiziyle ilgili ayrıntılı günlükler içerir. Bu seçenek, oluşturulan dosyanın boyutunu önemli ölçüde artırabilir, ancak IntelliSense sorunlarını tanılamak için genellikle gereklidir. |
| **Tanılamayı dosyaya kaydet** düğmesi | yok | Dosya adı isteminde bulunarak günlüğü bir metin dosyasına kaydeder. |
| **Tanılamayı panoya kopyala** düğmesi | yok | Günlüğün tamamını panoya yerleştirir; Bu işlem günlüğün boyutuna bağlı olarak biraz zaman alır. |

![Python seçenekleri iletişim kutusu, Tanılama sekmesi](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Etkileşimli Windows seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Python**  >  **Etkileşimli Windows** sekmesi.)

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Betikler** | yok | Başlangıç betikleri için tüm ortamlar için Etkileşimli pencerelere **uygulanacak** genel bir klasör belirtir. Bkz. [Başlangıç betikleri.](python-environments-window-tab-reference.md#startup-scripts) Ancak, bu özelliğin şu anda çalışmay olduğunu unutmayın. |
| **Yukarı/aşağı oklar gezinme geçmişi** | Açık | Etkileşimli pencerede geçmiş arasında gezinmek için ok **tuşlarını** kullanır. Bunun yerine Etkileşimli pencerenin çıkışında gezinmek için ok **tuşlarını kullanmak** üzere bu ayarın temizlerini kullanın. |
| **Tamamlama modu** | **Yalnızca işlev çağrıları olmadan ifadeleri değerlendirme** | Etkileşimli pencerede bir ifadede kullanılabilir üyeleri  belirleme işlemi, geçerli tamamlanmamış ifadenin değerlendirilmesi gerektirerek yan etkilerin veya işlevlerin birden çok kez çağrılmalarına neden olabilir. Yalnızca işlev çağrıları **olmadan ifadeleri değerlendir** varsayılan ayarı, bir işlevi çağıran ifadeleri dışlar, ancak diğer ifadeleri değerlendirir. Örneğin, değerlendirir ancak `a.b` `a().b` değerlendirmez.  **Hiçbir zaman ifadeleri** değerlendirme, öneriler için yalnızca normal IntelliSense altyapısını kullanarak tüm yan etkileri önlemektedir. **Tüm ifadeleri değerlendir,** yan etkilere bakılmaksızın önerileri almak için ifadenin tamamlandıktan sonra değerlendirilir. |
| **Statik analiz önerilerini gizleme** | Kapalı | Ayar olduğunda, yalnızca ifade değerlendirerek alınan önerileri görüntüler. Tamamlanma modu değeriyle **birleştirilmişse** **hiçbir zaman ifadeleri değerlendirme,** Etkileşimli penceresinde kullanışlı **tamamlamalar görünmez.** |

![Python seçenekleri iletişim kutusu, Etkileşimli Windows sekmesi](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Dil sunucusu seçenekleri

(**Araçlar** > **Seçenekler** > **Python** > **Dil sunucusu** sekmesi.)

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Typeshed'den tamamlamaları devre dışı bırakma** | Kapalı | Visual Studio IntelliSense normalde standart kitaplık ve üçüncü taraf kitaplıkları için hem Python 2 hem de Python 3 için tür ipuçlarını bulmak için Typeshed'in paketlenmiş bir sürümünü *(bir dizi .pyi* dosyası) kullanır. Bu seçeneğin ayarlanmamış olması, paketlenmiş TypeShed davranışını devre dışı bırakır. |
| **Özel Typeshed yolu** | (boş) | Ayarlanırsa, Visual Studio paketlenmiş sürümü yerine bu yolda Typeshed dosyalarını kullanır. **Typeshed'den tamamlamaları devre dışı bırak ayarlanırsa** yoksayın. |

![Python seçeneklerinde dil Visual Studio Araçları seçeneğinin ve sağ bölmede Dil Sunucusu seçeneklerinin gösterildiği Visual Studio Araçları Seçenekleri iletişim kutusunun ekran görüntüsü.](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Gelişmiş Python düzenleyicisi seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **Python**  >  **Gelişmiş** sekmesi.)

### <a name="completion-results"></a>Tamamlama Sonuçları

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Üye tamamlama, üyelerin kesişimlerini görüntüler** | Kapalı | Ayarlandıktan sonra, yalnızca tüm olası türler tarafından desteklenen tamamlamaları gösterir. |
| **Arama dizesine göre listeyi filtreleme** | Açık | Siz yazarak tamamlama önerilerinin filtresini uygular (varsayılan olarak işaretlidir). |
| **Tüm tanımlayıcılar için tamamlamaları otomatik olarak göster** | Açık | Hem düzenleyicide hem de Etkileşimli pencerelerde tamamlamaları devre dışı bırakmak için bu **seçeneğin temizlerini** kullanın. |

### <a name="selection-in-completion-list"></a>Tamamlama Listesinde Seçim

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Aşağıdaki karakterleri yazarak işlendi** | **{}\[\]().,:;+-*/%&&#124;^~=<> #@\\** | Bu karakterler genellikle bir tamamlama listesinden seçen bir tanımlayıcıyı takip eder, bu nedenle yalnızca bir karakter yazarak tamamlamayı işlemek kullanışlıdır. Listeyi istediğiniz gibi kaldırabilir veya listeye belirli karakterler ekleyebilirsiniz.  |
| **Geçerli tamamlama işlemelerini girin** | Açık | Ayarlandıktan sonra **Enter** tuşu seçili durumdaki tamamlamayı yukarıdaki karakterlerde olduğu gibi seçer ve uygular (ancak **Enter** için bir karakter mevcut değil, bu nedenle doğrudan listeye giriliktir!). |
| **Tam olarak yazıldı sözcüğün sonuna Enter tarak yazarak yeni satır ekleme** | Kapalı | Varsayılan olarak, tamamlama açılan menüsünde görünen sözcüğün tamamını girer ve **Enter** tuşuna bassanız, bu tamamlamayı işlersiniz. Bu seçeneği ayarlayarak, tanımlayıcıyı yazmayı tamamladığınızda, yeni bir **satır ekler gibi** tamamlama işlemleri etkili bir şekilde tamamlanır. |

### <a name="miscellaneous-options"></a>Çeşitli seçenekler

| Seçenek | Varsayılan | Description |
| --- | --- | --- |
| **Dosyalar açıkken anahat oluşturma moduna gir** | Açık | Python kod dosyasını açarken düzenleyicide Visual Studio ana hat özelliğini otomatik olarak aç. |
| **Kaldırılan REPL istemlerini Yapıştır** | Açık | **>>>** Yapıştırılmış metinden kaldırır ve **..** . ' yi, **etkileşimli** pencereden düzenleyiciye kolay bir şekilde aktarmaya izin verir. Diğer kaynaklardan yapıştırırken bu karakterleri saklamanız gerekiyorsa bu seçeneği temizleyin. |
| **Türlere göre renk adları** | Açık | Python kodunda sözdizimi renklendirmesini sunar. |

![Python düzenleyici seçenekleri iletişim kutusu, Gelişmiş sekmesi](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Yazı tipleri ve renkler seçenekleri

(**Ortam**  >  **Metin düzenleyici** grubu Içindeki **yazı tipleri ve renkler** sekmesi.)

Python seçeneklerinin adları **Python** ile önek olarak eklenir ve kendine açıklayıcı bir şekilde yapılır. tüm Visual Studio renk temaları için varsayılan yazı tipi 10 pt Consolas regular (kalın değildir). Varsayılan renkler temaya göre farklılık gösterir. Genellikle, varsayılan ayarlarla metin okumayı zorlaştırdıysanız bir yazı tipi veya rengi değiştirirsiniz.

![Python yazı tipi ve renk seçenekleri](media/options-fonts-and-colors.png)
