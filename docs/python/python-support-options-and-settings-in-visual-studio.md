---
title: Python için seçenekler ve ayarlar
description: Python kodu ve projeleriyle ilgili Visual Studio çeşitli ayarlara yönelik bir başvuru.
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
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 283e3a8474c9d7b301dd00fa7dcc0443a4a15e0c5c0a453c0c90709507c022cd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121245791"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio Python için seçenekler

Python seçeneklerini görüntülemek için, **Araçlar**  >  **Seçenekler** menü komutunu kullanın, **tüm ayarları göster** ' in seçili olduğundan emin olun ve ardından **Python**' a gidin:

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

**Metin düzenleyici**  >  **Python**  >  **Gelişmiş** sekmesinde ve   >  **metin düzenleyici** grubunun içindeki ortam **yazı tipi ve renkler** sekmesinde ek Python 'a özgü seçenekler de vardır.

> [!Note]
> **Deneysel** Grup, hala geliştirme aşamasında olan ve burada açıklanmayan özellikler için seçenekler içerir. Bunlar genellikle [Microsoft blogu 'Ndaki Python mühendisliğinde](https://devblogs.microsoft.com/python/)gönderilerde ele alınmıştır.

## <a name="general-options"></a>Genel seçenekler

(**Araçlar**  >  **Seçenekler**  >  **Python** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Sanal ortamlar oluştururken Çıkış Penceresi göster**| Açık | **Çıkış** penceresinin görünmesini engellemek için işaretini kaldırın. |
| **Paketleri yüklerken veya kaldırırken Çıkış Penceresi göster** | Açık | **Çıkış** penceresinin görünmesini engellemek için işaretini kaldırın. |
| **Ortam oluşturmak için bildirim çubuğunu göster** | Açık | *yalnızca Visual Studio 2019.* bu seçenek ayarlandığında ve kullanıcı *requirements.txt* veya *ortam....................... Visual Studio..* |
| **Paketleri yüklemek için bildirim çubuğunu göster** | Açık | *yalnızca Visual Studio 2019.* bu seçenek ayarlandığında ve kullanıcı bir *requirements.txt* dosyası içeren (ve varsayılan genel ortamı kullanmayan) bir proje açtığında, bu gereksinimleri geçerli ortamda yüklü paketlerle karşılaştırır Visual Studio. herhangi bir paket eksikse Visual Studio bu bağımlılıkları yüklemek için bir istem görüntüler. |
| **Paket yöneticilerini her zaman yönetici olarak çalıştır** | Kapalı | `pip install`Tüm ortamlar için her zaman ve benzer Paket Yöneticisi işlemlerini yükseltir. paketler yüklenirken, ortam dosya sisteminin *c:\Program Files* gibi korumalı bir alanında yer alıyorsa, yönetici ayrıcalıklarına Visual Studio sorar. Bu istem içinde, yalnızca bir ortam için install komutunu her zaman yükseltmeyi seçebilirsiniz. Bkz. [Paketler sekmesi](python-environments-window-tab-reference.md#packages-tab). |
| **İlk kullanımda tamamlanma DB 'yi otomatik olarak oluştur** | Açık | *Visual Studio 2017 sürüm 15,5 ve önceki sürümleri ve bir ıntellisense veritabanı kullanılırken daha sonraki sürümler için geçerlidir.* Onu kullanan kodu yazdığınızda, bir kitaplık için veritabanının tamamlanmasını önceliklendirir. Daha fazla bilgi için bkz. [IntelliSense sekmesi](python-environments-window-tab-reference.md?view=vs-2017&preserve-view=true#intellisense-tab). |
| **Sistem genelinde PYTHONPATH değişkenlerini yoksay** | Açık | Visual Studio, ortamlar ve projelerde arama yollarını belirtmek için daha doğrudan bir yol sağladığından, varsayılan olarak PYTHONPATH yoksayılır. Ayrıntılar için bkz. [arama yolları](search-paths.md) . |
| **Bağlı dosyalar eklenirken arama yollarını Güncelleştir** | Açık | Ayarlandığında, bir projeye [bağlı dosya](managing-python-projects-in-visual-studio.md#linked-files) eklemek, IntelliSense 'in bağlantılı dosyanın klasörünün içeriğini tamamlanma veritabanına dahil edebilmesi için [arama yollarına](search-paths.md) ekler. Bu tür içerikleri tamamlama veritabanından dışlamak için bu seçeneği temizleyin. |
| **İçeri aktarılan modül bulunamadığında uyar** | Açık | İçeri aktarılan bir modülün Şu anda kullanılabilir olmadığını bildiğiniz halde kod işlemini etkilemediği durumlarda uyarıları bastırmak için bu seçeneği temizleyin. |
| **Tutarsız Girintiyi şöyle raporla** | **Uyarılar** | Python yorumlayıcı kapsamı belirlemek için uygun girintiye bağlı olduğundan, varsayılan olarak Visual Studio kodlama hatalarını gösterebilen tutarsız girintili girintiler algıladığında uyarılar verir. Bu tür durumlarda programın çıkmasına neden olan, daha sıkı olması için **hatalara** ayarlanır. Bu davranışı tamamen devre dışı bırakmak için **değil**' i seçin. |
| **Anketi/haberleri denetle** | **Haftada bir kez** | *Visual Studio 2017 ve öncesi.* Visual Studio, Python ile ilgili anketler ve haber öğeleri varsa, bir web sayfası içeren bir pencereyi açmasına izin verme sıklığını ayarlar. Seçenekler **hiçbir** şekilde, **günde bir** kez, **haftada** bir ve **ayda bir** kez. |
| **Kalıcı olarak gizli iletişim kutularını Sıfırla** düğmesi | yok | Farklı iletişim kutuları **bunu bir daha gösterme** gibi seçenekler sağlar. Bu seçenekleri temizlemek ve iletişim kutularının yeniden görüntülenmesine neden olmak için bu düğmeyi kullanın. |

::: moniker range="vs-2017"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python seçenekleri iletişim kutusu, Genel sekmesi](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda seçenekleri

(**Araçlar** > **Seçenekler** > **Python** > **Conda** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Conda çalıştırılabilir yolu** | adet | Python iş yüküne dahil olan varsayılan Miniconda yüklemesine güvenmek yerine *conda.exe* yürütülebilirinin tam yolunu belirtir. Burada başka bir yol verilirse, bu, kayıt defterinde belirtilen varsayılan yükleme ve diğer conda.exe yürütülebilirlerin önüne geçer. Anaconda veya Miniconda 'ın daha yeni bir sürümünü el ile yüklüyorsanız veya varsayılan 64-bit dışında bir 32-bit ayırıcı kullanmak istiyorsanız bu ayarı değiştirebilirsiniz. |

![Python seçeneklerinde ve sağ bölmede gösterilen conda çalıştırılabilir yolu alanına Visual Studio Araçları seçenekleri iletişim kutusunun ekran görüntüsü.](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Hata ayıklama seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Python**  >  **Hata ayıklama** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Hata olduğunda çalıştırmadan önce sor** | Açık | Ayarlandığında, hata içeren kodu çalıştırmak istediğinizi onaylamanızı ister. Uyarıyı devre dışı bırakmak için bu seçeneği temizleyin. |
| **İşlem anormal bir şekilde çıkıldığında girişi bekle**<br/><br/>**İşlem normal şekilde çıkıldığında girişi bekle** | Açık (her ikisi için) | Visual Studio çalıştırmalarının kendi konsol penceresinde başlattığı bir Python programı. Varsayılan olarak, pencere, programın nasıl çıkdığına bakmaksızın kapatmadan önce bir tuşa basmanız için bekler. Bu istemi kaldırmak ve pencereyi otomatik olarak kapatmak için bu seçeneklerden birini veya her ikisini temizleyin. |
| **Hata ayıklama çıkışı penceresinde t program çıktısı** | Açık | program çıkışını ayrı bir konsol penceresinde ve Visual Studio **çıkış** penceresinde görüntüler. Çıktıyı yalnızca ayrı konsol penceresinde göstermek için bu seçeneği temizleyin. |
| **Sıfırın çıkış kodu ile SystemExit özel durumuyla kes** | Kapalı | Ayarlanırsa, bu özel durum üzerinde hata ayıklayıcıyı sonlandırır. Temiz olduğunda hata ayıklayıcısı hata ayıklayıcıdan hatasız olarak çıkar. |
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

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Analiz günlüklerini dahil edin** | Açık | Tanılamayı bir dosyaya kaydederken veya düğmeleri kullanarak panoya kopyalarken yüklü Python ortamlarının analiziyle ilgili ayrıntılı günlükler içerir. Bu seçenek, oluşturulan dosyanın boyutunu önemli ölçüde artırabilir, ancak IntelliSense sorunlarını tanılamak için genellikle gereklidir. |
| **Tanılamayı dosyaya kaydet** düğmesi | yok | Dosya adı isteminde bulunarak günlüğü bir metin dosyasına kaydeder. |
| **Tanılamayı panoya kopyala** düğmesi | yok | Günlüğün tamamını panoya yerleştirir; Bu işlem günlüğün boyutuna bağlı olarak biraz zaman alır. |

![Python seçenekleri iletişim kutusu, Tanılama sekmesi](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Etkileşimli Windows seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Python**  >  **Etkileşimli Windows** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Betikler** | yok | Başlangıç betikleri için tüm ortamlar için Etkileşimli pencerelere **uygulanacak** genel bir klasör belirtir. Bkz. [Başlangıç betikleri.](python-environments-window-tab-reference.md#startup-scripts) Ancak, bu özelliğin şu anda çalışmay olduğunu unutmayın. |
| **Yukarı/aşağı oklar gezinme geçmişi** | Açık | Etkileşimli pencerede geçmiş arasında gezinmek için ok **tuşlarını** kullanır. Bunun yerine Etkileşimli pencerenin çıkışında gezinmek için ok **tuşlarını kullanmak** üzere bu ayarın temizlerini kullanın. |
| **Tamamlama modu** | **Yalnızca işlev çağrıları olmadan ifadeleri değerlendirme** | Etkileşimli pencerede bir ifadede kullanılabilir üyeleri  belirleme işlemi, geçerli tamamlanmamış ifadenin değerlendirilmesi gerektirerek yan etkilerin veya işlevlerin birden çok kez çağrılmalarına neden olabilir. Yalnızca işlev çağrıları **olmadan ifadeleri** değerlendir varsayılan ayarı, bir işlevi çağıran ifadeleri dışlar, ancak diğer ifadeleri değerlendirir. Örneğin, değerlendirir ancak `a.b` `a().b` değerlendirmez.  **Hiçbir zaman ifadeleri** değerlendirme, öneriler için yalnızca normal IntelliSense altyapısını kullanarak tüm yan etkileri önlemektedir. **Tüm ifadeleri değerlendir,** yan etkilere bakılmaksızın önerileri almak için ifadenin tamamlandıktan sonra değerlendirilir. |
| **Statik analiz önerilerini gizleme** | Kapalı | Ayar olduğunda, yalnızca ifade değerlendirerek alınan önerileri görüntüler. Tamamlanma modu değeriyle **birleştirilmişse** **hiçbir zaman ifadeleri değerlendirme,** Etkileşimli penceresinde kullanışlı **tamamlamalar görünmez.** |

![Python seçenekleri iletişim kutusu, Etkileşimli Windows sekmesi](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Dil sunucusu seçenekleri

(**Araçlar** > **Seçenekler** > **Python** > **Dil sunucusu** sekmesi.)

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Typeshed'den tamamlamaları devre dışı bırakma** | Kapalı | Visual Studio IntelliSense normalde standart kitaplık ve hem Python 2 hem de Python 3 için üçüncü taraf kitaplıklara ait tür ipuçlarını bulmak için Typeshed'in paketlenmiş bir sürümünü *(bir dizi .pyi* dosyası) kullanır. Bu seçeneğin ayarlanmamış olması, paketlenmiş TypeShed davranışını devre dışı bırakır. |
| **Özel Typeshed yolu** | (boş) | Ayarlanırsa, Visual Studio paketlenmiş sürümü yerine bu yolda Typeshed dosyalarını kullanır. **Typeshed'den tamamlamaları devre dışı bırak ayarlanırsa** yoksayın. |

![Python seçeneklerinde dil Visual Studio Araçları ve sağ bölmede gösterilen Dil Sunucusu seçeneklerinin seçili olduğu Visual Studio Araçları Seçenekleri iletişim kutusunun ekran görüntüsü.](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Gelişmiş Python düzenleyicisi seçenekleri

(**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **Python**  >  **Gelişmiş** sekmesi.)

### <a name="completion-results"></a>Tamamlama Sonuçları

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Üye tamamlama, üyelerin kesişimlerini görüntüler** | Kapalı | Ayarlandıktan sonra, yalnızca tüm olası türler tarafından desteklenen tamamlamaları gösterir. |
| **Arama dizesine göre listeyi filtreleme** | Açık | Siz yazarak tamamlama önerilerinin filtresini uygular (varsayılan olarak işaretlidir). |
| **Tüm tanımlayıcılar için tamamlamaları otomatik olarak göster** | Açık | Hem düzenleyicide hem de Etkileşimli pencerelerde tamamlamaları devre dışı bırakmak için bu **seçeneğin temizlerini** kullanın. |

### <a name="selection-in-completion-list"></a>Tamamlama Listesinde Seçim

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Aşağıdaki karakterleri yazarak işlendi** | **{}\[\]().,:;+-*/%&&#124;^~=<> #@\\** | Bu karakterler genellikle bir tamamlama listesinden seçen bir tanımlayıcıyı takip eder, bu nedenle yalnızca bir karakter yazarak tamamlamayı işlemek kullanışlıdır. Listeyi istediğiniz gibi kaldırabilir veya listeye belirli karakterler ekleyebilirsiniz.  |
| **Geçerli tamamlama işlemelerini girin** | Açık | Ayarlandıktan sonra **Enter** tuşu seçili durumdaki tamamlamayı yukarıdaki karakterlerde olduğu gibi seçer ve uygular (ancak **Enter** için bir karakter mevcut değil, bu nedenle doğrudan listeye giriliktir!). |
| **Tam olarak yazıldı sözcüğün sonuna Enter tarak yazarak yeni satır ekleme** | Kapalı | Varsayılan olarak, tamamlama açılan menüsünde görünen sözcüğün tamamını girer ve **Enter** tuşuna bassanız, bu tamamlamayı işlersiniz. Bu seçeneği ayarladığınızda, tanımlayıcıyı yazmayı tamamladığınızda tamamlamaları etkili bir şekilde işlersiniz; **örneğin, Enter** yeni bir satır ekler. |

### <a name="miscellaneous-options"></a>Çeşitli Seçenekler

| Seçenek | Varsayılan | Açıklama |
| --- | --- | --- |
| **Dosyalar açıkken açıklama modu girin** | Açık | Python kod Visual Studio açılırken düzenleyicide otomatik olarak Visual Studio özelliğini açın. |
| **Yapıştır kaldırılan REPL istemleri** | Açık | Yapıştırilen **>>>** **metinden** ve ... kaldırır ve Etkileşimli  penceresinden düzenleyiciye kolayca kod aktarımına olanak sağlar. Diğer kaynaklardan yapıştırıyorsanız bu karakterleri korumanız gerekirse bu seçeneğin dışında tutmanız gerekir. |
| **Türlere göre renk adları** | Açık | Python kodunda söz dizimi renklendirmeyi sağlar. |

![Python düzenleyicisi seçenekleri iletişim kutusu, gelişmiş sekme](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Yazı Tipleri ve Renkler seçenekleri

(**Ortam**  >  **Metin Düzenleyici grubunun** içindeki Yazı Tipleri **ve Renkler** sekmesi.)

Python seçeneklerinin adlarının hepsi Python ön **eklidir** ve kendi kendine açıklayıcıdır. Tüm renk temaları için varsayılan Visual Studio 10 pt Consolas normaldir (kalın değildir). Varsayılan renkler temaya göre değişiklik gösterir. Genellikle, varsayılan ayarlarla metin okumanın zor olduğunu bulursanız yazı tipini veya rengi değiştirirsiniz.

![Python yazı tipi ve renk seçenekleri](media/options-fonts-and-colors.png)
