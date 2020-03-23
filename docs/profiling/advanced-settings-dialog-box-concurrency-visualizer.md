---
title: Gelişmiş Ayarlar İletişim Kutusu (Eşzamanlı Görüntüleyici) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa9d6658ae14c4b84aae9361f73e4701e758f975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911218"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Gelişmiş Ayarlar iletişim kutusu (Eşzamanlı Görüntüleyici)
Eşzamanlılık Görselleştiricisi'ndeki **Gelişmiş Ayarlar** iletişim kutusunu kullanarak, izlemelerin nasıl toplandığını denetleyebilirsiniz.  İletişim kutusunda semboller, Just My Code, arabelleğe alma, filtreleme, CLR olayları, işaretçiler, sağlayıcılar ve dosyalar için sekmeler vardır.

## <a name="symbols"></a>Simgeleri
 EşzamanlıLık Görselleştiricisi, Visual Studio Debugger ile aynı sembol ayarlarını kullanır. Eşzamanlılık Görselleştiricisi, performans verileriyle ilişkili çağrı yığınlarını çözmek için ayarları kullanır.  İzlemeleri işlerken, EşzamanlıLık Görselleştiricisi ayarlar sayfasında belirtilen sembol sunucularına erişir.  Bu verilere ağ üzerinden erişildiğinde, izleme işleme yavaşlar.  Sembolleri çözmek için gereken süreyi azaltmak için sembolleri yerel olarak önbelleğe alabilirsiniz. Semboller karşıdan yüklenmişse, Visual Studio bunları yerel önbellekten yükler.

## <a name="just-my-code"></a>Yalnızca Kendi Kodum
 Varsayılan olarak, Sadece Kodum kümesidir. *exe* ve . Visual Studio'daki geçerli çözümle ilişkili *dll* dosyaları. Eşzamanlılık Görselleştiricisi, çağrı yığınlarını filtrelemek için Kodum özelliğini kullandığınızda bu dosya kümesini değerlendirir. Yalnızca Kodum sekmesinde, '' içeren dizinler ekleyebilirsiniz. *exe* ve . *dll* dosyaları Eşzamanlılık Görselleştiricisi'nin Yalnızca Kodum için kullandığı konumlara yönlendirir.

 Yolların yolları. *exe* ve . *dll* dosyaları, izleme toplandığında izleme dosyasında depolanır.  Bu ayarı değiştirmek, önceden toplanan izlemeleri etkilemez.

## <a name="buffering"></a>Tamponlama
 Eşzamanlılık Görselleştiricisi, bir izleme topladığı zaman Windows için Olay İzleme (ETW) kullanır.  ETW, olayları depolarken çeşitli arabellekler kullanır.  Varsayılan ETW arabellek ayarları tüm durumlarda en uygun olmayabilir ve bazı durumlarda, kayıp olaylar gibi sorunlara neden olabilir.  ETW arabellek ayarlarını yapılandırmak için Arabelleğe Alma sekmesini kullanabilirsiniz. Daha fazla bilgi için [olay izleme](/windows/win32/etw/event-tracing-portal) ve [EVENT_TRACE_PROPERTIES yapısına](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties)bakın.

## <a name="filter"></a>Filtre
 Filtre sekmesinde, EşzamanlıLık Görselleştiricisi'nin topladığı olaylar kümesini seçebilirsiniz. Olayların bir alt kümesinin seçilmesi, raporlarda görüntülenen veri türlerini sınırlar, her izlemenin boyutunu azaltır ve izlemeleri işlemek için gereken süreyi azaltır.

### <a name="clr-events"></a>CLR olayları
 Ortak Dil Çalışma Zamanı (CLR) tarafından oluşturulan olaylar, Eşzamanlılık Görselleştiricisinin yönetilen çağrı yığınlarını çözmesini sağlar.  CLR olaylarının koleksiyonunu devre dışı düşürürseniz, izleme boyutu azalır, ancak bazı çağrı yığınları çözülmez.  Sonuç olarak, bazı CPU iş parçacığı etkinliği yanlış kategorize edilebilir.

### <a name="collect-for-native-processes"></a>Yerel işlemler için toplama
 Varsayılan olarak, CLR olayları yalnızca yönetilen bir işlem profilli olduğunda toplanır, çünkü bunlar normalde yerel işlemler için gereksizdir.  Bazı durumlarda (örneğin, yerel bir işlem CLR'yi barındırırken), yerel bir işlem için CLR olayları toplamanız gerekebilir.  Bu durumda, **Yerel İşlemler için Topla** onay kutusunu seçin.

### <a name="disable-rundown-events"></a>Özeti devre dışı
 CLR iki sağlayıcıdan olaylar oluşturur: çalışma süresi ve özeti.  CLR çalışma zamanı olaylarını toplamak, ancak eski olayları toplamaktan kaçınmak istiyorsanız, **Özeti Devre Dışı Düşür** onay kutusunu seçin.  Bu, koleksiyon tarafından oluşturulan izleme dosyasının boyutunu azaltır, ancak bazı yığınlar çözülmeyebilir. Daha fazla bilgi için [CLR ETW Sağlayıcıları'na](/dotnet/framework/performance/clr-etw-providers)bakın.

### <a name="sample-events"></a>Örnek olaylar
 İş parçacığı yürütme ile ilişkili çağrı yığınları toplamak için örnek olayları kullanabilirsiniz. Bu olaylar, geçerli işlemde çalıştırılan iş parçacıkları için milisaniyede yaklaşık bir kez toplanır. Örnek olayların koleksiyonunu devre dışı düşürürseniz, toplanan izlemenin boyutu azalır, ancak iş parçacığı yürütmeyle ilişkili çağrı yığınlarını görüntüleyemezsiniz.

### <a name="gpu-events"></a>GPU etkinlikleri
 GPU olayları DirectX tarafından oluşturulan olaylardır. GPU olaylarının koleksiyonunu devre dışı düşürürseniz, toplanan izlemenin boyutu azalır, ancak Kullanım görünümünde herhangi bir GPU Etkinliği veya İş İş parçacığı görünümünde DirectX Engine etkinliğini görüntüleyemezsiniz.

### <a name="file-io-events"></a>Dosya G/Ç olayları
 Dosya G/Ç olayları, geçerli işlem adına diske erişimi temsil eder.  Dosya G/Ç olaylarını devre dışı düşürürseniz, izlemenin boyutu küçülür, ancak İş Parçacıkları Görünümü disk kanalları veya Disk İşlemleri hakkında herhangi bir bilgi bildirmez.

## <a name="markers"></a>İşaretler
 **İşaretçiler** sekmesinde, Eşzamanlılık Görselleştiricisinde İşaretçiler olarak gösterilen ETW sağlayıcıları kümesini yapılandırabilirsiniz.  İşaretçi koleksiyonunu önem düzeyine ve ETW kategorisine göre de filtreleyebilirsiniz.  [Eşzamanlı Görselleştirici SDK](../profiling/concurrency-visualizer-sdk.md) kullanıyorsanız ve kendi Marker sağlayıcınızı kullanıyorsanız, Iş Parçacıkları Görünümü'nde görünmesi için buraya kaydedebilirsiniz.

### <a name="add-a-new-provider"></a>Yeni bir sağlayıcı ekleme
 Kodunuz Eşzamanlı [Görselleştirici SDK](../profiling/concurrency-visualizer-sdk.md) kullanıyorsa veya <xref:System.Diagnostics.Tracing.EventSource> kuralı izleyen ETW olayları oluşturuyorsa, bu olayları bu iletişim kutusuna kaydederek Eşzamanlılık Görselleştiricisinde görüntüleyebilirsiniz.

 **Ad** alanında, sağlayıcı tarafından oluşturulan olay türlerini açıklayan bir ad girin.  **GUID** alanında, bu sağlayıcıyla ilişkili GUID'i girin. (BIR GUID her ETW sağlayıcısıile ilişkilidir.)

 İsteğe bağlı olarak, kategori veya önem düzeyine bağlı olarak bu sağlayıcıdan gelen olayları filtreleyip filtrelemeyeceğiniz belirtebilirsiniz.  Eşzamanlı Görselleştirici SDK kategorilerini temel almak için kategori alanını kullanabilirsiniz.  Bunu yapmak için, virgülle sınırlandırılmış kategoriler veya kategoriler aralıkları dizisini girin.  Bu, gösterilen geçerli sağlayıcıdaki olayların kategorilerini belirtir.  Bir <xref:System.Diagnostics.Tracing.EventSource> sağlayıcı ekliyorsanız, Kategori alanını ETW anahtar kelimesine göre filtrelemek için kullanabilirsiniz.  Anahtar kelime bir bitmaskesi olduğundan, maskedeki hangi bitlerin ayarlanabileceğini belirtmek için virgülle sınırlı bir tamsayı dizesini kullanabilirsiniz. Örneğin, "1,2" birinci ve ikinci bitleri ayarlar ve bu ondalık olarak 6'ya çevirir.

 Önem düzeyi listesini, önem taşıyan olayları veya belirtilen değerden daha az Olan ETW düzeyini filtrelemek için kullanabilirsiniz.

### <a name="configure-an-existing-provider"></a>Varolan bir sağlayıcıyı yapılandırma
 Varolan bir sağlayıcıyla ilişkili ayarları sağlamak için, listede seçin ve ardından **sağlayıcıyı edin** düğmesini seçin.  Ad, GUID ve filtreleme ayarlarını değiştirebilirsiniz.

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Eşzamanlılık Visualizer raporlarından filtre işaretçisi verileri
 Belirli bir sağlayıcının verilerinin gelecekteki izlemelerde görünmesini istemiyorsanız, kaldırmak istediğiniz sağlayıcının yanındaki onay kutusunu temizleyin.

## <a name="files"></a>Dosyalar
 **Dosyalar** sekmesinde, her izleme toplandığında izleme dosyalarının depolandığı dizini belirtebilirsiniz.  Eşzamanlılık Görselleştiricisi topladığı her izleme için dört dosya oluşturur:

- Çekirdek modu olay izleme günlüğü (ETL) dosyası (<em>.</em> çekirdek.etl*)

- Bir kullanıcı modu olay izleme günlüğü dosyası (<em>.</em> user.etl*)

- Eşzamanlı Görüntüleyici Veri dosyası (<em>.</em> CVData*)

- Eşzamanlı Görüntüleyici İzleme dosyası (<em>.</em> CVTrace*)

  İki ETL dosyası ham izleme verilerini, iki Eşzamanlı Görselleştirici dosya ise işlenmiş verileri depolar.  Ham ETL dosyaları genellikle bir izleme işlendikten sonra kullanılmaz.  Analiz onay kutusunun **ardından Olay İzleme Günlüğü (ETL) dosyalarını** sil'i seçmek, diskinizde depolanan izleme verisi miktarını azaltır.

## <a name="see-also"></a>Ayrıca bkz.
- [Sadece benim kodum](../profiling/just-my-code-threads-view.md)
- [Eşzamanlı Görselleştirici işaretleri](../profiling/concurrency-visualizer-markers.md)