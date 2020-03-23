---
title: Python için seçenekler ve ayarlar
description: Visual Studio'da Python kodu ve projeleri ile ilgili çeşitli ayarlar için bir başvuru.
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302751"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio'da Python seçenekleri

Python seçeneklerini görüntülemek için **Araçlar** > **Seçenekleri** menü komutunu kullanın, tüm **ayarları göster'in** seçildiğinden emin olun ve ardından **Python'a**gidin:

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekme](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekme](media/options-general-2019.png)
::: moniker-end

Metin Düzenleyicisi > **Python** > **Advanced** sekmesinde ve Metin **Environment** >  **Düzenleyicisi**grubunda Çevre Yazı **Text Editor** **Tipleri ve Renkler** sekmesinde Python'a özgü ek seçenekler de vardır.

> [!Note]
> **Deney** grubu, hala geliştirilmekte olan ve burada belgelenmemiş özellikler için seçenekler içerir. Genellikle [Microsoft blogunda Python mühendislik](https://devblogs.microsoft.com/python/)mesajları nda ele alınmıştır.

## <a name="general-options"></a>Genel seçenekler

(**Araçlar** > **Seçenekleri** > **Python** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Sanal ortamlar oluştururken Çıktı Penceresini göster**| Açık | **Çıktı** penceresinin görünmesini önlemek için temizleyin. |
| **Paketleri yüklerken veya kaldırırken Çıktı Penceresini göster** | Açık | **Çıktı** penceresinin görünmesini önlemek için temizleyin. |
| **Ortamlar oluşturmak için bildirimler çubuğugöster** | Açık | *Sadece Visual Studio 2019.* Bu seçenek ayarlandığında ve kullanıcı *gereksinimler.txt* veya *environment.yml* dosyası içeren bir proje açtığında, Visual Studio varsayılan genel ortamı kullanmak yerine sırasıyla sanal bir ortam veya conda ortamı oluşturmak için öneriler içeren bir bilgi çubuğu görüntüler. |
| **Paketleri yüklemek için bildirimler çubuğunu göster** | Açık | *Sadece Visual Studio 2019.* Bu seçenek ayarlandığında ve kullanıcı *gereksinimler.txt* dosyası içeren bir proje açtığında (ve varsayılan genel ortamı kullanmıyorsa) Visual Studio bu gereksinimleri geçerli ortamda yüklü paketlerle karşılaştırır. Herhangi bir paket eksikse, Visual Studio bu bağımlılıkları yüklemek için bir istem görüntüler. |
| **Paket yöneticilerini her zaman yönetici olarak çalıştırın** | Kapalı | Tüm ortamlar `pip install` için her zaman paket yöneticisi işlemlerini yükseltir ve benzer şekilde sunar. Paketleri yüklerken, ortam dosya sisteminin *c:\Program Dosyaları*gibi korunan bir alanında bulunuyorsa Visual Studio yönetici ayrıcalıkları ister. Bu istekte, yükleme komutunu her zaman tek bir ortam için yükseltmeyi seçebilirsiniz. [Bkz. Paketler sekmesi.](python-environments-window-tab-reference.md#packages-tab) |
| **İlk kullanımda otomatik olarak tamamlama DB'si oluşturun** | Açık | *Visual Studio 2017 sürüm 15.5 ve daha önceki sürümler ve IntelliSense veritabanı kullanırken sonraki sürümler için geçerlidir.* Kullanan kod yazarken kitaplık için veritabanının tamamlanmasına öncelik verir. Daha fazla bilgi için [Intellisense sekmesine](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab)bakın. |
| **Sistem genelinde PYTHONPATH değişkenlerini yoksay** | Açık | VISUAL Studio ortamlarda ve projelerde arama yollarını belirtmek için daha doğrudan bir araç sağladığından PYTHONPATH varsayılan olarak yoksayılır. Ayrıntılar için [Arama yollarına](search-paths.md) bakın. |
| **Bağlantılı dosyalar eklerken arama yollarını güncelleştirme** | Açık | Ayarlandığında, projeye bağlı bir [dosya](managing-python-projects-in-visual-studio.md#linked-files) eklemek, IntelliSense'in bağlı dosyaklasörünün içeriğini tamamlama veritabanına dahil edilebilsin diye [Arama yollarını](search-paths.md) güncelleştirir. Bu tür içeriği tamamlama veritabanından hariç tutmak için bu seçeneği temizleyin. |
| **İthal modülü bulunamadığında uyar** | Açık | İçe aktarılan bir modülün şu anda kullanılmadığını, ancak kod çalışmasını başka şekilde etkilemediğini bildiğinizde uyarıları bastırmak için bu seçeneği temizleyin. |
| **Tutarsız girintiyi** | **Uyarılar** | Python yorumlayıcısı kapsamı belirlemek için uygun girintiye büyük ölçüde bağlı olduğundan, Visual Studio varsayılan olarak kodlama hatalarını gösterebilecek tutarsız girintiler algıladığında uyarılar daalır. Bu gibi durumlarda programın çıkmasına neden olan **hatalar** daha da katı olarak ayarlayın. Bu davranışı tamamen devre dışı kılabilir, **Don't'u**seçin. |
| **Anket/haber olup yok** | **Haftada bir kez** | *Visual Studio 2017 ve daha önce.* Varsa Visual Studio'nun Python ile ilgili anketler ve haber öğeleriiçeren bir web sayfası içeren bir pencere açmasına izin verme sıklığını ayarlar. Seçenekler **Asla**, **Günde bir kez**, haftada bir **kez**, ve ayda **bir kez**. |
| **Tüm kalıcı olarak gizlenmiş iletişim düğmelerini sıfırla** | yok | Farklı iletişim kutuları bana **bunu tekrar gösterme**gibi seçenekler sağlar. Bu seçenekleri temizlemek ve iletişim lerin yeniden görünmesine neden olmak için bu düğmeyi kullanın. |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekme](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekme](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda seçenekleri

(**Araçlar** > **Seçenekleri** > **Python** > **Conda** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Conda yürütülebilir yol** | (boş) | Python iş yüküyle birlikte varsayılan Miniconda yüklemesine güvenmek yerine *conda.exe* çalıştırılabilir'e kesin bir yol belirtir. Burada başka bir yol verilirse, varsayılan yüklemeden ve kayıt defterinde belirtilen diğer conda.exe yürütülebilirlerinden önce gelir. Anaconda veya Miniconda'nın daha yeni bir sürümünü el ile yüklerseniz veya varsayılan 64 bit dağıtım yerine 32 bit dağıtım kullanmak istiyorsanız bu ayarı değiştirebilirsiniz. |

![Python seçenekleri iletişim kutusu, Dil sunucusu sekmesi](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Hata ayıklama seçenekleri

(**Araçlar** > **Seçenekleri** > **Python** > Hata**Ayıklama** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Hatalar olduğunda çalıştırmadan önce komut istemi** | Açık | Ayarlandığında, hatalar içeren kod çalıştırmak istediğinizi onaylamanızı ister. Uyarıyı devre dışı kakmak için bu seçeneği temizleyin. |
| **İşlem anormal bir şekilde çıktığında girişi bekleyin**<br/><br/>**İşlem normal çıktığınızda girişi bekleyin** | On (her ikisi için de) | Visual Studio'dan başlayan bir Python programı kendi konsol penceresinde çalışır. Varsayılan olarak, pencere, programın nasıl çıktığına bakılmaksızın bir anahtarı kapatmadan önce basmanızı bekler. Bu istemi kaldırmak ve pencereyi otomatik olarak kapatmak için, bu seçeneklerden birini veya her ikisini de temizleyin. |
| **Hata Ayıklama Çıkış penceresine Tee program çıktısı** | Açık | Program çıktısını hem ayrı bir konsol penceresinde hem de Visual Studio **Çıktı** penceresinde görüntüler. Çıktıyı yalnızca ayrı konsol penceresinde göstermek için bu seçeneği temizleyin. |
| **Sıfır çıkış kodu ile SystemExit özel durumu sonu** | Kapalı | Ayarlanırsa, bu özel durum hata ayıklama durur. Temizlendiğinde, hata ayıklayıcı kırılmadan çıkar. |
| **Python standart kitaplığı hata ayıklama etkinleştirme** | Kapalı | Hata ayıklama sırasında standart kitaplık kaynak koduna adım atmayı mümkün kılar, ancak hata ayıklayıcının başlaması için gereken süreyi artırır.|
| **Fonksiyon iade değerini göster** | Açık | *Sadece Visual Studio 2019.* **Yerel ler** penceresinde işlev dönüş değerlerini görüntüler ve hata ayıklamadaki (F10) işlev çağrısının üzerinden adım |
| **Eski hata ayıklama kullanma** | Kapalı | *Sadece Visual Studio 2019.* Visual Studio'ya eski hata ayıklamayı varsayılan olarak kullanmasını bildirir. Daha fazla bilgi için [bkz: Hata Ayıklama - Eski hata ayıklama'yı kullanın.](debugging-python-in-visual-studio.md#use-the-legacy-debugger) |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Hata ayıklama sekmesi](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Hata ayıklama sekmesi](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Tanılama seçenekleri

(**Araçlar** > **Seçenekleri** > **Python** > **Tanılama** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Analiz günlüklerini ekleme** | Açık | Tanılamaları bir dosyaya kaydederken veya düğmeleri kullanarak panoya kopyalarken yüklü Python ortamlarının analiziyle ilgili ayrıntılı günlükleri içerir. Bu seçenek, oluşturulan dosyanın boyutunu önemli ölçüde artırabilir, ancak genellikle IntelliSense sorunlarını tanılamak için gereklidir. |
| **Tanılamayı dosya düğmesine kaydetme** | yok | Dosya adı ister, ardından günlüğü bir metin dosyasına kaydeder. |
| **Tanılamayı pano düğmesine kopyalama** | yok | Günlüğün tamamını panoya yerleştirir; bu işlem, günlüğün boyutuna bağlı olarak biraz zaman alabilir. |

![Python seçenekleri iletişim kutusu, Tanılama sekmesi](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Etkileşimli Windows seçenekleri

(**Araçlar** > **Seçenekleri** > **Python** > **Etkileşimli Windows** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Betikler** | yok | Tüm ortamlar için **Etkileşimli** pencerelere uygulanacak başlangıç komut dosyaları için genel bir klasör belirtir. [Başlangıç komut dosyalarını](python-environments-window-tab-reference.md#startup-scripts)görün. Ancak, bu özelliğin şu anda çalışmadığını unutmayın. |
| **Yukarı/aşağı oklar geçmişi gezinir** | Açık | **Etkileşimli** pencerede geçmişarasında gezinmek için ok tuşlarını kullanır. **Etkileşimli** pencerenin çıktısı içinde gezinmek için ok tuşlarını kullanmak için bu ayarı temizleyin. |
| **Tamamlama modu** | **Yalnızca işlev çağrısı olmayan ifadeleri değerlendirin** | **Etkileşimli** penceredeki bir ifadede kullanılabilir üyeleri belirleme işlemi, yan etkilerin veya işlevlerin birden çok kez çağrılabilir, geçerli tamamlanmamış ifadenin değerlendirilmesi gerektirebilir. Varsayılan ayar, **Yalnızca işlev çağrısı olmayan ifadeleri değerlendirir,** işlevi çağıran görünen ifadeleri dışlar, ancak diğer ifadeleri değerlendirir. Örneğin, değerlendirir `a.b` ama değil. `a().b`  **İfadeleri asla değerlendirmeyin,** öneriler için yalnızca normal IntelliSense motorlarını kullanarak tüm yan etkileri önler. **Tüm ifadeleri değerlendirin,** yan etkileri ne olursa olsun öneriler elde etmek için ifadenin tamamını değerlendirir. |
| **Statik analiz önerilerini gizleme** | Kapalı | Ayarlandığında, yalnızca ifadeyi değerlendirerek elde edilen önerileri görüntüler. **Tamamlama modu** değeri yle **birleştirilirse, ifadeleri asla değerlendirmeyin,** **Etkileşimli** pencerede yararlı tamamlanma lar görünmez. |

![Python seçenekleri iletişim kutusu, Etkileşimli Windows sekmesi](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Dil sunucusu seçenekleri

(**Araçlar** > **Seçenekleri** > **Python** > Dil **sunucu** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Typeshed'deki tamamlamaları devre dışı** | Kapalı | Visual Studio IntelliSense normalde standart kitaplık ve python 2 ve Python 3 için üçüncü taraf kitaplıkları için tür ipuçları bulmak için *Typeshed(.pyi* dosyaları kümesi) bir paket sürümünü kullanır. Bu seçeneğin ayarlanması, birlikte verilen TypeShed davranışını devre dışı kılabilir. |
| **Özel Yazı yolu** | (boş) | Ayarlanırsa, Visual Studio paketlenmiş sürümü yerine bu yolda Typeshed dosyaları kullanır. **Typeshed'deki tamamlanmaları devre dışı bırak'** a ayarlıysa yoksay. |

![Python seçenekleri iletişim kutusu, Dil sunucusu sekmesi](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Gelişmiş Python düzenleyici seçenekleri

(**Araçlar** > **Seçenekleri** > **Metin Editörü** > **Python** > **Gelişmiş** sekmesi.)

### <a name="completion-results"></a>Tamamlama Sonuçları

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Üye tamamlama, üyelerin kesişme lerini görüntüler** | Kapalı | Ayarlandığında, yalnızca tüm olası türler tarafından desteklenen tamamlanmaları gösterir. |
| **Arama dizelerine göre filtre listesi** | Açık | Siz yazarken tamamlama önerilerinin filtrelemesini uygular (varsayılan işaretlenir). |
| **Tüm tanımlayıcılar için otomatik olarak tamamlamaları gösterir** | Açık | Hem düzenleyici hem de **Etkileşimli** pencerelerdeki tamamlamaları devre dışı kakmak için bu seçeneği temizleyin. |

### <a name="selection-in-completion-list"></a>Tamamlama Listesinde Seçim

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Aşağıdaki karakterleri yazarak taahhüt** | **{}\[\]().,,:;+-*/%&&#124;^~=<> #@\\** | Bu karakterler genellikle bir tamamlama listesinden seçilebilen bir tanımlayıcıyı izler, bu nedenle yalnızca bir karakter yazarak tamamlamayı işlemek uygundur. Listeye istediğiniz gibi belirli karakterleri kaldırabilir veya ekleyebilirsiniz.  |
| **Girin geçerli tamamlama taahhüteder** | Açık | Ayarlandığında, **Enter** tuşu yukarıdaki karakterlerde olduğu gibi şu anda seçilen tamamlamayı seçer ve uygular (ancak tabii ki, **enter** için bir karakter yoktur, bu yüzden doğrudan listeye giremezsiniz!). |
| **Tam olarak yazılan sözcüğün sonunda enter'a yeni satır ekleme** | Kapalı | Varsayılan olarak, tamamlanma açılır penceresinde görünen sözcüğün tamamını yazar ve **Enter**tuşuna baslarsanız, bu tamamlamayı taahhüt elersiniz. Bu seçeneği ayarlayarak, **Enter'un** yeni bir satır eklemesi gibi tanımlayıcıyı yazmayı bitirdiğinizde tamamlamaları etkili bir şekilde adarsınız. |

### <a name="miscellaneous-options"></a>Çeşitli Seçenekler

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Dosyalar açıldığında anahat modunu girin** | Açık | Python kod dosyasını açarken Visual Studio'nun düzenleyicideki anahat özelliğini otomatik olarak açın. |
| **Kaldırılan REPL istemlerini yapıştır** | Açık | **>>>** Yapıştırılan metinden, **Etkileşimli** pencereden düzenleyiciye kolay kod aktarımı sağlayan ve **...** kaldırır. Diğer kaynaklardan yapıştırırken bu karakterleri saklamanız gerekiyorsa bu seçeneği temizleyin. |
| **Türlere göre renk adları** | Açık | Python kodunda sözdizimi boyamayı sağlar. |

![Python düzenleyici seçenekleri iletişim kutusu, gelişmiş sekme](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Yazı Tipleri ve Renkler seçenekleri

( **Metin Düzenleyicisi** grubunda**Çevre** > **Yazı Tipleri ve Renkler** sekmesi.)

Python seçeneklerinin adlarının tümü **Python** ile önceden belirlenmişve kendi kendini açıklar. Tüm Visual Studio renk temaları için varsayılan yazı tipi 10pt Consolas düzenli (kalın değil). Varsayılan renkler teme göre değişir. Genellikle, varsayılan ayarlarla metni okumayı zorbulursanız, yazı tipini veya rengi değiştirirsiniz.

![Python yazı tipi ve renk seçenekleri](media/options-fonts-and-colors.png)
