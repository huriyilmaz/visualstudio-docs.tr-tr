---
title: Gelişmiş ayarlar Iletişim kutusu (eşzamanlılık görselleştiricisi) | Microsoft Docs
description: İzleme içeriğini denetlemek için eşzamanlılık görselleştiricisi içindeki gelişmiş ayarları kullanın. Semboller, Yalnızca kendi kodum, arabelleğe alma ve daha fazlası için sekmeler vardır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc7d3464fd05b1fe99fcbfa8773e64bca4cb95e7
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205508"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Gelişmiş ayarlar iletişim kutusu (eşzamanlılık görselleştiricisi)
Eşzamanlılık Görselleştiricisinin **Gelişmiş ayarlar** iletişim kutusunu kullanarak, izlemelerin nasıl toplandığını kontrol edebilirsiniz.  İletişim kutusunda semboller, Yalnızca kendi kodum, arabelleğe alma, filtreleme, CLR olayları, işaretçiler, sağlayıcılar ve dosyalar için sekmeler bulunur.

## <a name="symbols"></a>Simgeleri
 Eşzamanlılık görselleştiricisi, Visual Studio hata ayıklayıcı ile aynı sembol ayarlarını kullanır. Eşzamanlılık görselleştiricisi, performans verileriyle ilişkili çağrı yığınlarını çözümlemek için ayarları kullanır.  İzleme işlerken eşzamanlılık görselleştiricisi, Ayarlar sayfasında belirtilen sembol sunucularına erişir.  Bu verilere bir ağ üzerinden erişildiğinde izleme işlemi yavaşlar.  Sembolleri çözümlemek için gereken süre miktarını azaltmak için sembolleri yerel olarak önbelleğe alabilirsiniz. Semboller indirildiyse, Visual Studio bu dosyaları yerel önbellekten yükler.

## <a name="just-my-code"></a>Yalnızca Kendi Kodum
 Varsayılan olarak, Yalnızca kendi kodum kümesidir. *exe* ve. Visual Studio 'daki geçerli çözümle ilişkili *DLL* dosyaları. Eşzamanlılık görselleştiricisi, çağrı yığınlarını filtrelemek için Yalnızca kendi kodum özelliğini kullandığınızda bu dosya kümesini değerlendirir. Yalnızca kendi kodum sekmesinde, içeren dizinleri ekleyebilirsiniz. *exe* ve. Yalnızca kendi kodum için eşzamanlılık görselleştiricisi tarafından kullanılan konumlara *DLL* dosyaları.

 Öğesinin yolları. *exe* ve. izleme toplandığında *DLL* dosyaları izleme dosyasında depolanır.  Bu ayarın değiştirilmesi, daha önce toplanan izlemeleri etkilemez.

## <a name="buffering"></a>Ara
 Eşzamanlılık görselleştiricisi bir izleme toplarken Windows için olay Izleme (ETW) kullanır.  ETW, olayları depolayan gibi çeşitli arabellekler kullanır.  Varsayılan ETW arabellek ayarları her durumda en uygun olmayabilir ve bazı durumlarda kayıp olayları gibi sorunlara neden olabilir.  ETW arabelleği ayarlarını yapılandırmak için arabelleğe alma sekmesini kullanabilirsiniz. Daha fazla bilgi için bkz. [olay izleme](/windows/win32/etw/event-tracing-portal) ve  [EVENT_TRACE_PROPERTIES yapısı](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties).

## <a name="filter"></a>Filtre
 Filtre sekmesinde, eşzamanlılık görselleştiricisi tarafından toplanan olay kümesini seçebilirsiniz. Olayların bir alt kümesini seçmek raporlarda görüntülenen veri türlerini sınırlar, her izlemenin boyutunu azaltır ve izlemeleri işlemek için gereken süreyi azaltır.

### <a name="clr-events"></a>CLR olayları
 Ortak dil çalışma zamanı (CLR) tarafından oluşturulan olaylar, yönetilen çağrı yığınlarını çözümlemek için eşzamanlılık Görselleştiricisini etkinleştirir.  CLR olayları koleksiyonunu devre dışı bırakırsanız, izleme boyutu azaltılır ancak bazı çağrı yığınları çözümlenmeyecektir.  Sonuç olarak, bazı CPU iş parçacığı etkinlikleri yanlış kategorilere ayrılmıştır.

### <a name="collect-for-native-processes"></a>Yerel süreçler için topla
 Varsayılan olarak, CLR olayları yalnızca, yerel işlemler için genellikle gereksiz olduklarından, yönetilen bir işlem profili oluşturulduğunda toplanır.  Bazı durumlarda (örneğin, yerel bir işlem CLR 'yi barındırdığında), yerel bir işlem için CLR olayları toplamanız gerekebilir.  Bu durumda, **Yerel süreçler Için topla** onay kutusunu seçin.

### <a name="disable-rundown-events"></a>Özet olaylarını devre dışı bırak
 CLR iki sağlayıcıdan olay oluşturur: çalışma zamanı ve Özeti.  CLR çalışma zamanı olaylarını toplamak istiyorsanız ancak Özet olayları toplamayı önlemek istiyorsanız, Özet **olaylarını devre dışı bırak** onay kutusunu seçin.  Bu, koleksiyon tarafından oluşturulan izleme dosyasının boyutunu azaltır, ancak bazı yığınlar çözümlenmeyebilir. Daha fazla bilgi için bkz. [CLR ETW sağlayıcıları](/dotnet/framework/performance/clr-etw-providers).

### <a name="sample-events"></a>Örnek olaylar
 Örnek olayları, iş parçacığı yürütme ile ilişkili çağrı yığınlarını toplamak için kullanabilirsiniz. Bu olaylar, geçerli işlemde yürütülen iş parçacıkları için her milisaniyeye göre yaklaşık olarak toplanır. Örnek olaylar koleksiyonunu devre dışı bırakırsanız, toplanan izlemenin boyutu azaltılır, ancak iş parçacığı yürütme ile ilişkili çağrı yığınlarını görüntüleyemezsiniz.

### <a name="gpu-events"></a>GPU olayları
 GPU olayları DirectX tarafından oluşturulan olaylardır. GPU olayları koleksiyonunu devre dışı bırakırsanız, toplanan izlemenin boyutu azaltılır, ancak kullanım görünümünde veya Iş parçacığı görünümündeki DirectX motoru etkinliğinde herhangi bir GPU etkinliğini görüntüleyemezsiniz.

### <a name="file-io-events"></a>Dosya g/ç olayları
 Dosya g/ç olayları, geçerli işlem adına disk erişimlerini temsil eder.  Dosya g/ç olaylarını devre dışı bırakırsanız, izlemenin boyutu azalır, ancak Iş parçacıkları görünümü disk kanalları veya disk Işlemleriyle ilgili herhangi bir bilgi bildirmeyecektir.

## <a name="markers"></a>İşaretler
 **İşaretleyiciler** sekmesinde, eşzamanlılık görselleştiricisi içinde işaret olarak gösterilen etw sağlayıcıları kümesini yapılandırabilirsiniz.  Ayrıca, Işaret koleksiyonunu önem düzeyi ve ETW kategorisine göre filtreleyebilirsiniz.  [Eşzamanlılık Görselleştiricisi SDK 'sını](../profiling/concurrency-visualizer-sdk.md) kullanıyorsanız ve kendi işaretleyici sağlayıcınızı kullanıyorsanız, Iş parçacıkları görünümünde görünmesi için buraya kaydolabilirsiniz.

### <a name="add-a-new-provider"></a>Yeni Sağlayıcı Ekle
 Kodunuz [Eşzamanlılık Görselleştiricisi SDK 'sını](../profiling/concurrency-visualizer-sdk.md) kullanıyorsa veya KURALı izleyen ETW olayları oluşturursa <xref:System.Diagnostics.Tracing.EventSource> , bu olayları bu Iletişim kutusuna kaydederek eşzamanlılık görselleştiricisi içinde görüntüleyebilirsiniz.

 **Ad** alanına sağlayıcı tarafından oluşturulan olay türlerini açıklayan bir ad girin.  **GUID** alanına, bu sağlayıcıyla ilişkili GUID değerini girin. (Bir GUID, her ETW sağlayıcısıyla ilişkilendirilir.)

 İsteğe bağlı olarak, Bu sağlayıcıdan, kategoriye veya önem düzeyine göre olayların filtreleneceğini belirtebilirsiniz.  Eşzamanlılık Görselleştiricisi SDK kategorilerine göre filtrelemek için kategori alanını kullanabilirsiniz.  Bunu yapmak için, bir dizi kategori veya kategori aralığı girin.  Bu, geçerli sağlayıcıdaki gösterilecek olay kategorilerini belirtir.  <xref:System.Diagnostics.Tracing.EventSource>Sağlayıcı ekliyorsanız, ETW anahtar sözcüğüne göre filtrelemek için kategori alanını kullanabilirsiniz.  Anahtar sözcüğü bir bit maskesi olduğundan, maskede hangi bitlerin ayarlandığını belirtmek için virgülle ayrılmış tamsayılar dizesini kullanabilirsiniz. Örneğin, "1, 2" ilk ve ikinci bitleri ayarlar ve bu, ondalık olarak 6 ' ya çevirir.

 Önem düzeyi listesini, önemli veya ETW düzeyi belirtilen değerden daha az olan olayları filtrelemek için kullanabilirsiniz.

### <a name="configure-an-existing-provider"></a>Mevcut bir sağlayıcıyı yapılandırma
 Mevcut bir sağlayıcıyla ilişkili ayarları düzenlemek için listeden seçin ve ardından **Sağlayıcıyı Düzenle** düğmesini seçin.  Ad, GUID ve filtreleme ayarlarını değiştirebilirsiniz.

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Eşzamanlılık görselleştiricisi raporlarının işaret verilerini filtreleme
 Belirli bir sağlayıcının verilerinin gelecek izlemelerde görünmesini istemiyorsanız, kaldırmak istediğiniz sağlayıcının yanındaki onay kutusunu temizleyin.

## <a name="files"></a>Dosyalar
 **Dosyalar** sekmesinde, izleme dosyalarının her toplanışında depolanacağı dizini belirtebilirsiniz.  Eşzamanlılık görselleştiricisi topladığı her izleme için dört dosya üretir:

- Çekirdek modu olay izleme günlüğü (ETL) dosyası (<em>.</em> Kernel. etl *)

- Kullanıcı modu olay izleme günlük dosyası (<em>.</em> User. etl *)

- Eşzamanlılık görselleştiricisi veri dosyası (<em>.</em> CVData *)

- Eşzamanlılık görselleştiricisi Izleme dosyası (<em>.</em> CVTrace *)

  İki ETL dosyası ham izleme verilerini depolar ve iki eşzamanlılık görselleştiricisi dosyası işlenen verileri depolar.  Ham ETL dosyaları genellikle bir izleme işlendikten sonra kullanılmaz.  **Analiz sonrasında olay Izleme günlüğü (ETL) dosyalarını sil** onay kutusu seçildiğinde, diskinizde depolanan izleme verisi miktarı azalır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yalnızca kendi kodum](../profiling/just-my-code-threads-view.md)
- [Eşzamanlılık görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md)