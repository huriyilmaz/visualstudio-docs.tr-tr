---
title: Windows Mağazası uygulamaları için hata ayıklama oturumunda bir mağaza uygulamasının yürütülmesini denetleme (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9238bd4f42291af23a1279c9caa83f1039c8f249
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828609"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Microsoft Store uygulamaları için Visual Studio hata ayıklama oturumunda bir Store uygulamasının yürütülmesini denetleme (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hızlı başlangıç, Visual Studio hata ayıklayıcısında nasıl gezineceğinizi ve bir oturumdaki program durumunun nasıl görüntüleneceğini gösterir.

 Bu hızlı başlangıç, Visual Studio ve Visual Studio hata ayıklama oturumunda gezinme hakkında daha fazla bilgi edinmek isteyen geliştiriciler için Visual Studio ile hata ayıklamaya yeni olan geliştiricilere yöneliktir. Hata ayıklamanın bir resmini kendi kendine öğretmez. Örnek koddaki işlevler yalnızca bu konuda açıklanan hata ayıklama yordamlarını göstermek için tasarlanmıştır. İşlevler, uygulama veya işlev tasarımının en iyi yöntemlerini kullanmaz. Aslında, işlevleri ve uygulamanın kendisini, her şeyin hiç bir şey yapmadığınızı hızlı bir şekilde keşfedeceksiniz.

 Bu hızlı başlangıç 'nin bölümleri mümkün olduğunca bağımsız olacak şekilde tasarlandı, bu sayede zaten bildiğiniz bilgileri içeren herhangi bir bölümü atlayabilirsiniz. Örnek bir uygulama oluşturmanız da gerekmez. Ancak, bunu öneriyoruz ve işlemi mümkün olduğunca kolay hale sunuyoruz.

 **Hata ayıklayıcı klavye kısayolları.** Visual Studio hata ayıklayıcısında gezinti, hem fare hem de klavye için iyileştirilmiştir. Bu konudaki adımların birçoğu, parantez içinde klavye hızlandırıcıyı veya kısayol tuşunu içerir. Örneğin, (klavye: F5) F5 tuşunu yazmanın başladığı veya hata ayıklayıcının yürütülmesine devam ettiğini gösterir.

> [!NOTE]
> **Modül deseninin**
>
> Windows Mağazası uygulamaları, verileri ve işlevleri bir sayfada kapsüllemek için genellikle JavaScript *Modül modelini* kullanır. Modül stili, sayfa işlevselliğinin genel ad alanından ayrı tutulması için tek, kendi kendine yürütülen ve anonim bir kapanış kullanır. Bu konu *başlığında, bu*işlevi işlevini çağıracağız.

## <a name="in-this-topic"></a>Bu konuda
 Şunları yapmayı öğrenebilirsiniz:

 [Örnek uygulamayı oluşturma](#BKMK_Create_the_sample_app)

 [Ayarlama ve bir kesme noktasına çalıştırma, bir işleve adımla ve program verilerini İnceleme](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [İşlevlere Step, over ve out işlevleri](#BKMK_Step_into__over__and_out_of_functions)

 [Koşullu kesme noktası ayarlayın, imlece çalıştırın ve bir değişkeni görselleştirin](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Yerel öğeler penceresinde değişken verileri görüntüleme](#BKMK_View_variable_data_in_the_Locals_window)

- [Bir nesnenin değişken verilerini ve prototip zincirini görüntüleme](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Kapsam zinciri verilerini İnceleme](#BKMK_Examine_scope_chain_data)

  [Çağrı yığını penceresini kullanarak koda gitme](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

## <a name="create-the-sample-app"></a><a name="BKMK_Create_the_sample_app"></a> Örnek uygulamayı oluşturma
 Hata ayıklama kod ile ilgilidir, bu nedenle örnek uygulama yalnızca bir hata ayıklama oturumunun nasıl çalıştığını ve program durumunun nasıl incelendiğine görebileceğiniz bir kaynak dosyası oluşturmak için Windows Mağazası uygulamasının çerçevesini kullanır. Çağırabileceğiniz tüm kodlar `module` default.js dosyasının işlevinden çağırılır. Hiçbir denetim eklenmez ve hiçbir olay işlenmiyor.

1. **Boş bir JavaScript Windows Mağazası uygulaması oluşturun.** Visual Studio'yu açın. Giriş sayfasında, **Yeni proje** bağlantısı ' nı seçin. **Yeni proje** iletişim kutusunda, **yüklü** listede **JavaScript** ' i seçin ve ardından **Windows Mağazası**' nı seçin. Proje şablonları listesinde **boş uygulama**' yı seçin. Visual Studio yeni bir çözüm ve proje oluşturur ve default.htm dosyasını kod düzenleyicisinde görüntüler.

    Sayfasına yüklenen komut dosyalarını unutmayın.

   - `base.js`Ve `ui.js` dosyaları, **JavaScript için Windows kitaplığı**oluşturur. JavaScript için Windows kitaplığı, JavaScript kullanarak Windows Mağazası uygulamaları oluşturmayı kolaylaştıran bir JavaScript ve CSS dosyaları kümesidir. Uygulamanızı oluşturmak için bunu HTML, CSS ve Windows Çalışma Zamanı birlikte kullanırsınız.

   - Kodunuz `default.js`  dosyada başlar.

2. **default.js kaynak dosyasını açın.** Çözüm Gezgini ' de, **js** düğümünü açın ve öğesini seçin `default.js` .

3. **Sayfa içeriğini örnek kodla değiştirin.** Dosyadaki tüm içeriği silin `default.js` . Şu bağlantıyı izleyin: [hata ayıklayıcı gezinti örnek kodu (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md)ve sonra JavaScript bölümünde listelenen kodu panoya kopyalayın. (Bu hızlı başlangıç sayfasına dönmek için tarayıcıda veya yardım görüntüleyicisinde **geri** 'yi seçin.) Visual Studio düzenleyicisinde, kodu şimdi boş öğesine yapıştırın `default.js` . Dosyayı kaydetmek için **CTRL + S** 'yi seçin.

   Artık bu konudaki örneklerle birlikte takip edebilirsiniz.

## <a name="set-and-run-to-a-breakpoint-step-into-a-function-and-examine-program-data"></a><a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Ayarlama ve bir kesme noktasına çalıştırma, bir işleve adımla ve program verilerini İnceleme
 Bir hata ayıklama oturumu başlatmak için en yaygın yol **, hata ayıklama menüsünden** **hata ayıklamayı Başlat** ' ı seçin (klavye: F5). Uygulama başlar ve kesme noktasına ulaşılana kadar yürütmeyi sürdürür, yürütmeyi el ile askıya alın, bir özel durum oluşur veya uygulama sonlanır.

 Hata ayıklayıcıda yürütme askıya alındığında, değişkende fare 'yi duraklatarak bir veri ipucunda etkin bir değişkenin değerini görüntüleyebilirsiniz.

 Uygulamanın yürütülmesini askıya aldıktan sonra (hata ayıklayıcıya bölünmesi olarak da bilinir), program kodunun geri kalanının ne şekilde yürütüldüğünü kontrol edersiniz. Satır satır hattına devam edebilir, bir işlev çağrısından işlevin kendisini taşıyabilirsiniz veya çağrılan bir işlevi tek bir adımda yürütebilirsiniz. Bu yordamlara uygulama aracılığıyla atlama adı verilir. Ayrıca, uygulamanın standart yürütmesini, ayarlamış olduğunuz bir sonraki kesme noktasına veya imlecinizi yerleştirdiğiniz çizgiye da sürdürebilirsiniz. Hata ayıklama oturumunu dilediğiniz zaman durdurabilirsiniz. Hata ayıklayıcı, gerekli temizleme işlemlerini gerçekleştirmek ve yürütmeden çıkmak için tasarlanmıştır.

### <a name="example-1"></a><a name="BKMK_Example_1"></a> Örnek 1
 Bu örnekte, ' deki bir kesme noktasını, `module` `default.js` Kullanıcı deyimlerimizin Birincini çağırdığı gibi olarak ayarlarsınız. Sonra işlevin içine adımlayın, hata ayıklayıcı veri ipuçlarında değişken değerlerini görüntüleyin ve ardından hata ayıklamayı durdurun.

1. **Bir kesme noktası ayarlayın.** Çağrısından hemen sonra gelen bildirimde bir kesme noktası ayarlayın `callTrack = "module function";` `app.start()` . Kaynak kodu düzenleyicisinin gölgeli Cilt payının (klavye: imleci satıra konumlandırın ve **F9** tuşuna basın) satırını seçin.

    ![Example1 'de bir kesme noktası ayarlayın](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Kesme noktası simgesi cilt payı içinde görünür.

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5).

    Uygulama yürütülmeye başlar ve kesme noktasını ayarladığınız deyimden hemen önce yürütmeyi askıya alır. Cilt Paydaki geçerli çizgi simgesi konumunuzu tanımlar ve geçerli ifade vurgulanır.

    ![Kesme noktasında Çalıştır](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Artık uygulamanın yürütülmesini denetlemektir ve program deyimlerine adım adım ilerleyecek şekilde program durumunu inceleyebilirsiniz.

3. **İşlevine adımla.** **Hata Ayıkla** menüsünde, **Step** (klavye: **F11**) öğesini seçin.

    ![Kod satırına adımla](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Hata ayıklayıcının, işleve yapılan bir çağrı olan sonraki satıra taşındığını unutmayın `example1` . Yeniden **adımla** öğesini seçin. Hata ayıklayıcı işlevin ilk kod satırına gider `example1` . Vurgulanan satır yürütülmedi, ancak işlev çağrı yığınına yüklendi ve yerel değişkenler için bellek ayrıldı.

4. Bir kod satırına adım adım hata ayıklayıcı aşağıdaki eylemlerden birini gerçekleştirir:

   - Sonraki ifade çözümünüzdeki bir işleve bir çağrı değilse, hata ayıklayıcı deyimyi yürütür, sonraki ifadeye gider ve sonra yürütmeyi askıya alır.

   - İfade, çözümünüzde bir işleve yapılan çağrıdır, hata ayıklayıcı çağrılan işlevin ilk satırına gider ve sonra yürütmeyi askıya alır.

     Çıkış noktasına ulaşıncaya kadar deyimlerinin içine ilermeye devam edin `example1` . Hata ayıklayıcı işlevin kapanış küme ayracını vurgular.

5. **Veri ipuçlarında değişken değerlerini görüntüleyin.** Çıkış noktasına ulaşıncaya kadar deyimlerinin içine ilermeye devam edin `example1` . Hata ayıklayıcı işlevin kapanış küme ayracını vurgular. Bir değişken adı üzerinde fareyi duraklattığınızda, değişkenin adı ve değeri bir veri ipucunda görüntülenir.

    ![Veri ipucunda değişken değerlerini görüntüleme](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **CallTrack değişkeni için bir izleme ekleyin.** `callTrack`Bu hızlı başlangıç boyunca bu değişken, örneklerde çağrılan işlevleri göstermek için kullanılır. Değişkenin değerini görüntülemeyi kolaylaştırmak için, izleme penceresi ekleyin. Düzenleyicide değişken adını seçin ve sonra kısayol menüsünden **Gözcü Ekle** ' yi seçin.

    ![Bir değişken izleyin](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Bir izleme penceresinde birden çok değişkeni izleyebilirsiniz. Veri ipucu pencerelerinin değerleri gibi izlenen değişkenlerin değerleri, her yürütme askıya alındığında güncelleştirilir. İzlenen değişkenleriniz hata ayıklama oturumları arasında kaydedilir.

7. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: **SHIFT + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="step-into-over-and-out-of-functions"></a><a name="BKMK_Step_into__over__and_out_of_functions"></a> İşlevlere Step, over ve out işlevleri
 Bir üst işlev tarafından çağrılan bir işleve adımlamayı sağlamak için, bir işlev üzerinde adımlamayı alt işlevi yürütür ve ardından çağırma işlevindeki yürütme, üst devam eden işlev olarak askıya alınır. İşlevin çalışma biçimini bildiğiniz ve yürütmenin Araştırdığınız sorunu etkilemediğinden emin olan bir işlev üzerinde ilersiniz.

 Bir işlev çağrısı içermeyen bir kod satırının üzerine adımlamak, satırı tıpkı satıra adımla benzer şekilde yürütür.

 Bir alt işlevin dışına atlama işlevi çalışmaya devam eder ve işlev çağıran işlevine döndüğünde yürütmeyi askıya alır. İşlevin geri kalanının önemli olmadığını belirlediğinizde uzun bir işlevin dışına ilerlemeyebilirsiniz.

 İşlev üzerinde hem atlama hem de atlama işlevi yürütün.

 ![Yönteme adımla, aşırı ve dışı Yöntemler](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a><a name="BKMK_Example_2"></a> Örnek 2
 Bu örnekte, işlevleri içine, üzerine ve dışına adımlayın.

1. **Modül işlevindeki Example2 işlevini çağırın.** İşlevini düzenleyin `module` ve aşağıdaki satırı `var callTrack = "module function"` ile değiştirin `example2();` .

     ![Example2 işlevini çağırma](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5). Hata ayıklayıcı, kesme noktasında yürütmeyi askıya alır.

3. **Kod satırının üzerinde adımla.** **Hata Ayıkla** menüsünde, **Atla** ' yı (klavye: F10) seçin. Hata ayıklayıcı, ifadeyi `var callTrack = "module function"` ifadeye adımla aynı şekilde yürütür.

4. **Example2 ve example2_a içine adımlayın.** İşleve adım eklemek için **F11** tuşuna basın `example2` . `example2`Çizgiye ulaşana kadar deyimlere adımla devam edin `var x = example2_a();` . Bir kez daha, giriş noktasına geçmek için bu satıra adımlayın `example2_a` . Öğesine dönene kadar her bir ifadeye adımla devam edin `example2_a` `example2` .

     ![İşlev üzerinde adımla](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5. **Bir işlevin üzerinde adımla.** İçindeki sonraki satırın `example2` `var y = example2_a();` temelde önceki satırla aynı olduğunu unutmayın. Bu satırın üzerinde güvenle ileredebilirsiniz. Sürdürme ' dan bu ikinci çağrıya geçmek için **F10** tuşunu seçin `example2` `example2_a` . `callTrack`Dizesinin `example2_a` işlevin iki kez yürütüldüğünü belirtir.

6. **İşlevin dışına adımla.** İşleve adım eklemek için **F11** tuşuna basın `example2_b` . Bunun `example2_b` çok farklı olduğunu unutmayın `example2_a` . İşlevin dışına geçmek için **hata ayıklama** menüsünde **Step Out** (klavye: **Shift + F11**) seçeneğini belirleyin. `callTrack`Değişkenin `example2_b` yürütüldüğünü ve hata ayıklayıcının devam eden noktaya döndürüldüğünü unutmayın `example2` .

7. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: **SHIFT + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Koşullu kesme noktası ayarlayın, imlece çalıştırın ve bir değişkeni görselleştirin
 Koşullu kesme noktası, hata ayıklayıcının yürütmeyi askıya almasına neden olan bir koşulu belirtir. Koşul, doğru veya yanlış olarak değerlendirilebilen herhangi bir kod ifadesiyle belirtilir. Örneğin, bir değişken belirli bir değere ulaştığında sık çağrılan bir işlevde program durumunu incelemek için koşullu bir kesme noktası kullanabilirsiniz.

 İmlece çalıştırmak, tek seferlik kesme noktası ayarlamaya benzer. Yürütme askıya alındığında, kaynakta bir satırı seçebilir ve seçilen satıra ulaşılana kadar yürütmeyi sürdürebilirsiniz. Örneğin, bir işlev içindeki bir döngüyle adımlamayı ve döngüdeki kodun doğru şekilde işlem gösterdiğini belirlemenizi sağlayabilirsiniz. Döngünün her tekrarında atlama yerine, döngü yürütüldükten sonra konumlandırılmış olan imlece çalıştırabilirsiniz.

 Bazen bir veri ipucunun veya diğer veri penceresinin satırında bir değişken değeri görüntülemek zordur. Hata ayıklayıcı, kaydırılabilir bir penceredeki değerin biçimli bir görünümünü sunan bir metin görselleştiricisi içinde dizeler, HTML ve XML görüntüleyebilir.

### <a name="example-3"></a><a name="BKMK_Example_3"></a> Örnek 3
 Bu örnekte, bir döngünün belirli bir yinelemesine bölmek için koşullu bir kesme noktası ayarlayın ve ardından döngüden sonra konumlandırılmış olan imlece çalıştırın. Ayrıca bir değişkenin değerini bir metin Görselleştirici içinde görüntüleyebilirsiniz.

1. **Modül işlevindeki Example3 işlevini çağırın.** İşlevi düzenleyin `module` ve satır ile takip eden çizgiyi değiştirin `var callTrack = "module function";` `example3();` .

     ![Example3 çağır](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: **F5**). Hata ayıklayıcı, işlev içindeki kesme noktasında yürütmeyi askıya alır `module` .

3. **Example3 işlevine adımla.** İşlevin giriş noktasına gitmek için **hata ayıklama** menüsünde (klavye: **F11**) **içine adımla** öğesini seçin `example3` . Bloğun bir veya iki döngüsü tekrarlanana kadar işlevine adımla devam edin `for` . Tüm 1000 yinelemeleriyle ilgili olarak size uzun bir süre geçtiğine göz atın.

4. **Koşullu kesme noktası ayarlayın.** Kod penceresinin sol cilt payından satıra sağ tıklayın `s += i.toString() + "\n";` ve sonra kısayol menüsünde **koşul** ' ı seçin.

     **Koşul** onay kutusunu seçin ve `i == 500;` metin kutusuna yazın. **True** seçeneğini belirleyin ve **Tamam**' ı seçin. Kesme noktası, döngünün 500. yinelemesinde değeri denetlemenizi sağlar `for` . Koşullu kesme noktası simgesini beyaz çarpı ile tanımlayabilirsiniz.

     ![Koşullu kesme noktası simgesi](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5. **Kesme noktasına çalıştırın.** **Hata Ayıkla** menüsünde **devam** ' ı (klavye: **F5**) seçin. `i`Geçerli değerinin 500 olduğunu doğrulamak için üzerinde ' i duraklatın `i` . Ayrıca, değişkenin `s` tek satır olarak temsil edildiği ve veri ipucu penceresinden çok daha uzun olduğunu unutmayın.

6. **Bir dize değişkenini görselleştirin.** Veri ipucunda büyüteç simgesine tıklayın `s` .

     Metin görselleştiricisi penceresi görünür ve dizenin değeri çok satırlı bir dize olarak sunulur.

     ![Hata ayıklama metin görselleştiricisi](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7. **İmleci imlece çalıştırın.** Satırı `callTrack += "->example3";` ve ardından kısayol menüsünde **Imlece Çalıştır** ' ı seçin (klavye: **CTRL + F10**). Hata ayıklayıcı döngü yinelemelerini tamamlar ve sonra işlemi satırdaki yürütmeyi askıya alır.

8. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: **SHIFT + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

### <a name="use-run-to-cursor-to-return-to-your-code-and-delete-a-breakpoint"></a><a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Koda geri dönmek ve bir kesme noktasını silmek için, Imlece için Çalıştır 'ı kullanma
 Microsoft 'tan veya üçüncü bir tarafa ait kitaplık koduna ihtiyacınız olduğunda imlecin imlece çalıştırılması çok yararlı olabilir. Kitaplık kodu üzerinden atlama bilgilendirici olabilir, ancak bu durum genellikle uzun zaman alabilir. Genellikle kendi kodunuzda daha fazla ilgileniyorsunuz. Bu alıştırmada nasıl yapılacağı gösterilmektedir.

1. **Uygulamada bir kesme noktası ayarlayın. çağrı başlatın.** `module`İşlevinde, satırda bir kesme noktası ayarlayın`app.start()`

2. **Kesme noktasında çalıştırın ve kitaplık işlevinde adımlayın.**

     ' De adım adım `app.start()` , düzenleyici içinde kodu görüntüler `base.js` . Birkaç satıra adımla.

3. **İşlevin üzerinde ve dışına adımla.** ' De (**F10**) ve Step of (SHIFT + F11) kodundan bir adım daha (F10) ve Step Out (**SHIFT + F11**) kodu üzerinde bir `base.js` değer ortaya çıkabilir ve başlangıç işlevinin uzunluğu, yapmak istediğiniz şeydir.

4. **İmleci kodunuza ayarlayın ve üzerinde çalıştırın.** `default.js`Kod düzenleyicisinde dosyasına dönün. Sonra ilk kod satırını seçin `app.start()` (bir yoruma veya boş bir satıra çalıştıramazsınız). Kısayol menüsünden **Imlece Çalıştır** ' ı seçin. Hata ayıklayıcı App. Start işlevini yürütmeye devam eder ve yürütme kesme noktasında askıya alınır.

## <a name="view-variable-data-in-the-locals-window"></a><a name="BKMK_View_variable_data_in_the_Locals_window"></a> Yerel öğeler penceresinde değişken verileri görüntüleme
 Yereller Windows, şu anda yürütülmekte olan işlevin kapsam zincirindeki parametrelerin ve değişkenlerin ağaç görünümüdür.

### <a name="view-variable-data-and-the-prototype-chain-of-an-object"></a><a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Bir nesnenin değişken verilerini ve prototip zincirini görüntüleme

1. **Bir dizi nesnesini modül işlevine ekleyin.** İşlevi düzenleyin `module` ve aşağıdaki satırı `var callTrack = "module function"` ile değiştirin `var myArray = new Array(1, 2, 3);`

     ![myArray tanımı](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: **F5**). Hata ayıklayıcı, kesme noktasında yürütmeyi askıya alır. Satıra adımla.

3. **Yereller penceresini açın.** **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin ve ardından **Yereller**' i seçin. (Klavye: alt + 4).

4. **Modül işlevindeki yerel değişkenleri inceleyin** Yereller Windows, şu anda yürütülmekte olan işlevin ( `module` işlev) değişkenlerini ağacın en üst düzey düğümleri olarak görüntüler. Bir işlev girdiğinizde, JavaScript tüm değişkenleri oluşturur ve bu değere bir değer verir `undefined` . İşlevinde tanımlanan işlevlerin metinleri bir değer olarak bulunur.

     ![Yerel öğeler penceresi](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5. **CallTrack ve myArray tanımlarında adım adım.** Yereller penceresinde callTrack ve myArray değişkenlerini bulun. İki tanım üzerinde (**F10**) adımlayın ve **değer** ve **tür** alanlarının değiştirildiğini görürsünüz. Yereller penceresi, son kesmeyi bu yana değiştirilen değişkenlerin değerlerini vurgular.

6. **MyArray nesnesini inceleyin** Değişkeni genişletin `myArray` . Dizinin her öğesi, nesnesinin devralma hiyerarşisini içeren **[Prototype]** düğümü listelenir `Array` . Bu düğümü genişletin.

     ![Yereller penceresinde prototip zinciri](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    - **Yöntemler** düğümü, nesnenin tüm yöntemlerini listeler `Array` .

    - **[Prototype]** düğümü, `Object` öğesinden türetilen nesnenin prototipini içerir `Array` . **[prototip]** düğümleri özyinelemeli olabilir. Bir nesne hiyerarşisindeki her üst nesne, alt öğesinin **[prototip]** düğümünde açıklanmıştır.

7. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: SHIFT + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="examine-scope-chain-data"></a><a name="BKMK_Examine_scope_chain_data"></a> Kapsam zinciri verilerini İnceleme
 Bir işlevin *kapsam zinciri* , etkin olan ve işlev tarafından erişilebilen tüm değişkenleri içerir. Genel değişkenler, şu anda yürütülmekte olan işlevi tanımlayan işlevde tanımlanmış nesneler (işlevler dahil) gibi, kapsam zincirinin bir parçasıdır. Örneğin, `callTrack` işlevinde tanımlanan değişkene, `module` `default.js` işlevinde tanımlı herhangi bir işlev tarafından ulaşılabilir `module` . Her kapsam Yereller penceresinde ayrı olarak listelenir.

- Şu anda yürütülmekte olan işlevin değişkenleri pencerenin üst kısmında listelenir.

- Kapsam zincirindeki her bir işlev kapsamının değişkenleri, işlev için bir **[Scope]** düğümünün altında listelenir. Kapsam işlevleri, geçerli işlevi, zincirinin en dıştaki işlevine tanımlayan işlevden zincirde sırasıyla sıralamayla listelenir.

- **[Globals]** düğümü, herhangi bir işlevin dışında tanımlanan genel nesneleri listeler.

  Kapsam zincirleri kafa karıştırıcı olabilir ve örnek olarak en iyi şekilde gösterilmiştir. Aşağıdaki örnekte, `module` işlevin kendi kapsamını nasıl oluşturduğunu ve bir kapanış oluşturarak başka bir kapsam düzeyi nasıl oluşturabileceğiniz hakkında bilgi alabilirsiniz.

### <a name="example-4"></a><a name="BKMK_Example_4"></a> Örnek 4

1. **Modül işlevindeki example4 işlevini çağırın.** İşlevini düzenleyin `module` ve aşağıdaki satırı `var callTrack = "module function"` ile değiştirin `example4()` :

     ![Example4 çağır](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: **F5**). Hata ayıklayıcı, kesme noktasında yürütmeyi askıya alır.

3. **Yereller penceresini açın.** Gerekirse, **Hata Ayıkla** menüsünde **Windows**' a gelin ve ardından **Yereller**' i seçin. (Klavye: **alt + 4**). Pencerenin, işlevindeki tüm değişkenleri ve işlevleri listelediğinden `module` ve ayrıca bir **[Globals]** düğümü içerdiğini unutmayın.

4. **Genel değişkenleri inceleyin.** **[Globals]** düğümünü genişletin. Genel içindeki nesneler ve değişkenler, JavaScript için Windows kitaplığı tarafından ayarlanmıştır. Kendi değişkenlerinizi genel kapsama ekleyebilirsiniz.

5. **Example4 Içine adımla ve yerel ve kapsam değişkenlerini İnceleme** İçine adımla (klavye: **F11**) `example4` işlevi. , `example4` `module` İşlevinde tanımlandığından, `module` işlev üst kapsam haline gelir. `example4` , işlevindeki işlevlerden herhangi birini çağırabilir `module` ve değişkenlerine erişebilir. Locals penceresinde **[Scope]** düğümünü genişletin ve işlevin aynı ve değişkenlerini içerdiğini unutmayın `module` .

     ![Example4 yönteminin kapsamları](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6. **Example4_a Içine adımla ve yerel ve kapsam değişkenlerini İnceleme** Çağrısına devam edin `example4` `example4_a` . Yerel değişkenlerin artık kimden olduğunu `example4_a` ve **[Scope]** düğümünün işlevin değişkenlerini tutmaya devam ettiğini unutmayın `module` . Değişkenleri etkin olsa bile `example4` , tarafından erişilemez `example4_a` ve artık kapsam zincirinin bir parçası değildir.

7. **MultiplyByA 'Ya adımla ve yerel ve kapsam değişkenlerini inceleyin** Geri kalan `example4_a` ve satıra adım adım `var x = multiplyByA(b);` .

     İşlev değişkeni, `multiplyByA` `multiplyClosure` bir *Kapanış*olan işleve ayarlanmış. `multiplyClosure` bir iç işlevi tanımlar ve döndürür, `multiplyXby` ve kendi parametresini ve değişkenini yakalar (kapatır). Bir kapanışda döndürülen iç işlevin dış işlevin verilerine erişimi vardır ve bu nedenle kendi kapsam düzeyini oluşturur.

     İçine adımlayın `var x = multiplyByA(b);` , `return a * b;` iç işlevdeki satıra geçiş yapabilirsiniz `multiplyXby` .

8. Yereller penceresinde, yalnızca parametresi ' `b` de yerel değişken olarak listelenir `multiplyXby` , ancak yeni bir **[Scope]** düzeyi eklenmiştir. Bu düğüm genişletiliyor, öğesinin `multiplyClosure` `a` ilk satırında çağrılan değişken dahil olmak üzere parametre, işlev ve değişkenlerini içerdiğini görürsünüz `multiplyXby` . İkinci **[Scope]** düğümüne hızlı bir denetim, bir sonraki satırda erişilen modül işlevi değişkenlerini ortaya koyar `multiplyXby` .

9. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: **SHIFT + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="navigate-to-code-by-using-the-call-stack-window"></a><a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Çağrı yığını penceresini kullanarak koda gitme
 Çağrı yığını, uygulamanın geçerli iş parçacığında yürütülen işlevlerle ilgili bilgileri içeren bir veri yapısıdır. Bir kesme noktasına ulaştığınızda, çağrı yığını penceresi yığında etkin olan tüm işlevlerin bir listesini görüntüler. Şu anda yürütülmekte olan işlev çağrı yığını pencere listesinin en üstünde bulunur. İş parçacığını Başlatan işlev listenin en altında bulunur. Between içindeki işlevler, başlatma işlevinden gelen çağrı yolunu geçerli işleve gösterir.

 Şu anda yürütülmekte olan işlevin çağrı yolunu göstermeye ek olarak, çağrı yığını penceresi kod düzenleyicisinde koda gitmek için kullanılabilir. Bu işlevsellik, birden çok dosya ile çalışırken ve belirli bir işleve hızlıca gitmek istediğinizde değerli olabilir.

### <a name="example-5"></a><a name="BKMK_Example_5"></a> Örnek 5
 Bu örnekte, Kullanıcı tanımlı beş işlevi içeren bir çağrı yolu içine adımlayın.

1. **Modül işlevindeki example5 işlevini çağırın.** İşlevi düzenleyin `module` ve satır ile takip eden çizgiyi değiştirin `var callTrack = "module function";` `example5();` .

     ![Example5 çağır](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2. **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: **F5**). Hata ayıklayıcı, modül işlevindeki kesme noktasında yürütmeyi askıya alır.

3. **Çağrı yığını penceresini açın.** **Hata Ayıkla** menüsünde **Windows**' u ve ardından **çağrı yığını** ' nı (klavye: alt + 7) seçin. Çağrı yığını penceresinde iki işlev gösterildiğine unutmayın:

    - **Genel kod** , `module` çağrı yığınının alt kısmındaki işlevin giriş noktasıdır.

    - **Anonim işlev** , `module` işlevin yürütmenin askıya alındığı satırı gösterir. Bu, çağrı yığınının en üstü.

4. **Example5_d işlevine ulaşmak için işlevlere adımlayın.** Example5_d işlevin giriş noktasına ulaşana kadar çağrı yolundaki çağrıları yürütmek için **hata ayıklama** menüsündeki (klavye: **F11**) **içine adımla** öğesini seçin. Bir işlev bir işlevi çağırdığı her seferinde, çağıran işlevin satır numarası kaydedilir ve çağrılan işlev yığının en üstüne yerleştirilir. Çağıran işlevin satır numarası, çağırma işlevinin yürütmeyi askıya aldığı noktasıdır. Sarı bir ok Şu anda yürütülmekte olan işleve işaret eder.

     ![Çağrı yığını penceresi](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5. **Example5_a koduna gitmek ve bir kesme noktası ayarlamak için çağrı yığını penceresini kullanın.** Çağrı yığını penceresinde, `example5_a` liste öğesini seçin ve ardından kısayol menüsünde **Kaynağa Git** ' i seçin. Kod Düzenleyicisi, imlecini işlevin dönüş satırında ayarlar. Bu satırda bir kesme noktası ayarlayın. Geçerli yürütme satırının değiştirilmediğini unutmayın. Yalnızca Düzenleyici imleci taşınır.

6. **İşlevlere adımlayın ve sonra kesme noktasına çalıştırın.** Adımla devam edin `example5_d` . İşlevinden geri döndüğünüzde, çağrı yığınının dışına alındığını unutmayın. Program yürütmeye devam etmek için **F5** tuşuna basın. Önceki adımda oluşturulan kesme noktasında durursunuz.

7. **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: **SHIFT + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir hata ayıklama oturumu başlatın (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [hızlı başlangıç: hata ayıklayıcı Gezintisi (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) [tetikleyici Windows Mağazası için geri alma, geri alma ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Visual Studio 'da hata](../debugger/debug-store-apps-in-visual-studio.md)
