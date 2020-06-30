---
title: IntelliTrace Özellikleri | Microsoft Docs
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ac7ca0e59a479aff3386486d2ceaf061038db68
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536584"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>IntelliTrace Özellikleri (C#, Visual Basic, C++)

Uygulamanızı kaydetmek için IntelliTrace 'i kullanabilirsiniz. bu sayede, durumunu (çağrı yığını ve yerel değişken değerleri) yürütmenin farklı noktalarında incelemenizi sağlayabilirsiniz. Her zamanki-IntelliTrace varsayılan olarak açıktır ve bilgi IntelliTrace 'in kayıt olduğunu **Olaylar** sekmesinin altındaki yeni **Tanılama araçları** penceresinde görebilirsiniz. bir olay seçin ve bu olay için kaydedilen çağrı yığınını ve yerelleri görmek Için **geçmiş hata ayıklamayı etkinleştir** ' e tıklayın.

Adım adım bir açıklama için bkz. [Izlenecek yol: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace Visual Studio Enterprise sürümünde kullanılabilir, ancak Visual Studio Professional veya topluluk sürümlerinde bulunmaz.

IntelliTrace 'in açık olduğunu onaylamak için **araçlar > seçenekler > IntelliTrace** seçenekleri sayfasını açın. **IntelliTrace 'ı etkinleştir** ayarı varsayılan olarak denetlenmelidir.

> [!NOTE]
> **IntelliTrace** seçenekleri sayfasındaki tüm ayarların kapsamı, tek tek projeler veya çözümler değil, bir bütün olarak Visual Studio. Bu ayarlarda yapılan bir değişiklik, tüm Visual Studio örnekleri, tüm hata ayıklama oturumları ve tüm projeler veya çözümler için geçerlidir.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a>IntelliTrace 'in kaydettiği olayları seçin (C#, Visual Basic)

Belirli IntelliTrace olayları için kayıt açma veya kapatma yapabilirsiniz.

Hata ayıklaması yapıyorsanız, hata ayıklamayı durdurun. IntelliTrace **> IntelliTrace olayları > araçlar > seçenekler**' e gidin. IntelliTrace 'in kaydetmesini istediğiniz olayları seçin.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a>Anlık görüntü topla (C#, Visual Basic, C++)

Bu varsayılan olarak etkin değildir, ancak IntelliTrace her kesme noktası ve hata ayıklayıcı adımı olayındaki uygulamanızın anlık görüntülerini yakalayabilir ve bu anlık görüntüleri bir geçmiş hata ayıklama oturumunda görüntüleyebilirsiniz. Anlık görüntü, tam uygulama durumlarınızın görünümünü sağlar. Anlık görüntülerin yakalanmasını etkinleştirmek için **araçlar > seçenekler > ıntellitrace > Genel**' e gidin ve **IntelliTrace anlık görüntülerini (yönetilen ve yerel)** seçin. Daha fazla bilgi için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md).

Anlık görüntüler Visual Studio Enterprise 2017 sürüm 15,5 ve üzeri sürümlerde kullanılabilir ve Windows 10 yıldönümü güncelleştirmesi veya üstünü gerektirir.  .NET Core ve ASP.NET Core uygulamaları için, Visual Studio Enterprise 2017 sürüm 15,7 gereklidir. Windows 'u hedefleyen yerel uygulamalar için Visual Studio Enterprise 2017 sürüm 15,9 Preview 2 gereklidir.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a>IntelliTrace olayları ve çağrı bilgilerini toplayın (C#, Visual Basic)

Bu varsayılan olarak etkin değildir, ancak IntelliTrace Yöntem çağrılarını olaylarla birlikte kaydedebilir. Yöntem çağrılarını toplamayı etkinleştirmek için **araçlar > seçenekler > ıntellitrace > Genel**' e gidin ve **IntelliTrace olayları ve çağrı bilgileri ' ni seçin (yalnızca yönetilen)**.

Çağrı bilgileri şu anda .NET Core ve ASP.NET Core uygulamaları için kullanılamaz.

Bu, çağrı yığını geçmişini görmenizi ve kodunuzda geri ve ileri doğru ilerlemenizi sağlar. IntelliTrace, yöntem adları, yöntem girişi ve çıkış noktaları gibi verileri ve belirli parametre değerlerini ve dönüş değerlerini kaydeder.

> [!TIP]
> Bu seçenek, önemli ölçüde ek yükü eklediğinden varsayılan olarak etkinleştirilmemiştir. IntelliTrace, uygulamanızın yaptığı her yöntem çağrısını ele almak zorunda kalmaz, ancak aynı zamanda ekranda gösterilmesi veya diske kalıcı hale geldiğinde çok daha büyük bir veri kümesiyle uğraşmak zorunda olur.
>
> IntelliTrace 'in kaydettiği olayların listesini sınırlayarak ve topladığınız modül sayısını en az bir olarak tutarak performans yükünü azaltabilirsiniz. Daha fazla bilgi için bkz. [arama bilgisi IntelliTrace 'in ne kadar kayıt olduğunu denetleme](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Gezinti cilt payını kullanma

Kod penceresinin solunda görünen gezinti payını kullanabilirsiniz. Gezinti cilt payını görmüyorsanız, **araçlar > seçenekler > ıntellitrace > gelişmiş**' e gidin ve **hata ayıklama modundayken gezinti cilt payını görüntüle**' yi seçin.

Gezinti cilt payı, geçmiş hata ayıklama modundaki Yöntem çağrıları ve olaylar aracılığıyla iletme ve geri ileretmenize olanak tanır. Geçmiş hata ayıklama hakkında daha fazla bilgi için bkz. [geçmiş hata ayıklama](../debugger/historical-debugging.md). Birkaç komuta sahiptir:

|Komut|Description|
|-|-|
|**Hata ayıklayıcı bağlamını burada ayarla**|Hata ayıklama bağlamını göründüğü çağrı zaman çerçevesi olarak ayarlayın.<br /><br /> Bu simge yalnızca geçerli çağrı yığınında görünür.|
|**Çağrı sitesine dön**|İşaretçiyi ve hata ayıklama bağlamını geçerli işlevin çağrıldığı yere geri taşıyın.<br /><br /> Canlı hata ayıklama modundaysanız, bu komut tarihinde geçmiş hata ayıklamayı açar. Özgün yürütme kesmesine geri gittiğinizde geçmiş hata ayıklama kapatılır ve canlı hata ayıklama açılır.|
|**Önceki çağrıya veya IntelliTrace olayına git**|İşaretçiyi ve hata ayıklama bağlamını önceki çağrıya veya olaya geri taşıyın.<br /><br /> Canlı hata ayıklama modundaysanız, bu komut geçmiş hata ayıklamayı açar.|
|**Adımla**|Şu anda seçili olan işleve adımla.<br /><br /> Bu komut yalnızca geçmiş hata ayıklama modundayken kullanılabilir.|
|**Sonraki çağrıya veya IntelliTrace olayına git**|İşaretçi ve hata ayıklama bağlamını, IntelliTrace verilerinin bulunduğu bir sonraki çağrıya veya olaya taşıyın.<br /><br /> Bu komut yalnızca geçmiş hata ayıklama modundayken kullanılabilir.|
|**Canlı moda git**|Canlı hata ayıklama moduna geri dönün.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>IntelliTrace içinde bir hat veya yöntem arayın

Metotları yalnızca Yöntem çağrı bilgileri etkinleştirildiğinde arayabilirsiniz. IntelliTrace geçmişine belirli bir satır veya yöntem için arama yapabilirsiniz. Hata ayıklayıcı yürütmesi durdurulduğunda, bağlam menüsünü görmek için işlevin gövdesinin içine sağ tıklayın ve **Bu satırı IntelliTrace Içinde ara** ' ya tıklayın veya **IntelliTrace içinde bu yöntemi**arayın.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a>Ne kadar çağrı bilgisi IntelliTrace kaydı olduğunu denetleme

Varsayılan olarak IntelliTrace, çözümünüz tarafından kullanılan tüm modüllerle ilgili bilgileri kaydeder. IntelliTrace 'i yalnızca sizi ilgilendiren modüller için çağrı bilgilerini kaydedecek şekilde ayarlayabilirsiniz. **Araçlar > seçenekler > ıntellitrace > modüller**' de dahil edilecek modülleri veya IntelliTrace 'ten dışlanacak modülleri belirtebilirsiniz. IntelliTrace yalnızca belirttiğiniz modüllerden kaynaklı olayları ve ilgilendiğiniz modüller içinde gerçekleşen yöntemi çağırır.

Birden çok modül eklemek için dizenin başında veya sonunda * joker karakterini kullanın. Modül isimleri için derleme adlarını değil dosya adlarını kullanın. Dosya yolları kabul edilmez.

Modül sayısını en düşük düzeyde tutmaya çalışın. Toplanabilecek daha az veri olduğundan daha iyi bir performans alırsınız. Ayrıca, alınacak daha az veri olduğu için Kullanıcı arabiriminde daha az gürültü da alırsınız.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a>IntelliTrace verilerini dosyaya kaydet (C#, Visual Basic, C++)

IntelliTrace 'in topladığı verileri, hata ayıklarken IntelliTrace **oturumunu > ıntellitrace > kaydetmek** ve uygulama bir kesme durumunda olduğu sırada kaydedebilirsiniz. Menü öğesi devre dışıdır ve uygulama hala çalışıyorsa veya hata ayıklamayı durdurduysanız veri IntelliTrace 'in topladığı verileri kaydedemeyeceksiniz.

IntelliTrace ' i **> ıntellitrace > Gelişmiş ' >** e giderek ve **IntelliTrace kayıtlarını bu dizinde depola**' yı seçerek bir dosyaya otomatik olarak kaydedilecek IntelliTrace 'i yapılandırabilirsiniz. Ayrıca oluşturulan dosya için bir küme boyutu yapılandırabilirsiniz. Bu, IntelliTrace 'in boş alan tükendiği eski verileri üzerine yazmasına neden olur. Visual Studio otomatik olarak kaydedildiğinde her IntelliTrace oturumu için iki dosya oluşturur ve Visual Studio barındırma işlemi (vshost.exe) açıktır.

> [!TIP]
> Disk alanından tasarruf etmek için, artık ihtiyacınız olmadığında dosyaları otomatik olarak kaydetmeyi devre dışı bırakın. Var olan tüm dosyalar silinmez. Bağlam menüsünden her zaman isteğe bağlı olarak dosya kaydedebilirsiniz.

IntelliTrace verilerini dosyaya kaydettiğinizde, IntelliTrace 'in topladığı her işlem için bir. iTrace dosyası alırsınız. Daha sonra **dosya > > açıp** Dosya Aç iletişim kutusundan. iTrace dosyasını seçerek, Visual Studio 'da. iTrace dosyasını açabilirsiniz. Daha fazla bilgi için bkz. [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Bloglar

[Visual Studio Enterprise 2015 ' de IntelliTrace](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Visual Studio 2015 ' de IntelliTrace kullanılarak canlı hata ayıklama için İzlenecek yol (metin Düzenleyicisi)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Visual Studio 2015 (Sosyal Kulübü) içinde IntelliTrace kullanılarak canlı hata ayıklama hakkında izlenecek yol](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[Visual Studio Enterprise 2015 ' deki IntelliTrace artık eklemeyi destekliyor!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[IntelliTrace tek başına toplayıcısı 'nı kullanarak bir Windows hizmetinden veri toplama](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[IntelliTrace toplama planını Düzenle](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[IntelliTrace kullanarak özel TraceSource ve hata ayıklama](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[Active Directory hesapları altında çalışan IntelliTrace tek başına toplayıcı ve uygulama havuzları](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Forumlar

[Visual Studio Hata Ayıklayıcısı](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Videolar

[IntelliTrace deneyimi](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Microsoft Visual Studio Ultimate 2015 ' de IntelliTrace ile geçmiş hata ayıklama](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
