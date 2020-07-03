---
title: Windows komut dosyası arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 141f3f0e60e797a4104c3e276775631f6e9196c5
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835413"
---
# <a name="windows-script-interfaces"></a>Windows Komut Dosyası Arabirimleri

Microsoft Windows komut dosyası arabirimleri, bir uygulamanın komut dosyası ve OLE Otomasyonu eklemesi için bir yol sağlar. Windows betiği kullanan komut dosyası Konakları, bileşenler arasında betikleri yönetmek için birden çok kaynak ve satıcının komut dosyası altyapılarını kullanabilir. Komut dosyasının kendisi (dil, sözdizimi, kalıcı biçim, yürütme modeli vb.), betik satıcısına bırakılır.

Windows komut dosyası belgeleri aşağıdaki bölümlere ayrılmıştır:

[Windows Betik Konakları](../winscript/windows-script-hosts.md)

[Windows Betik Motorları](../winscript/windows-script-engines.md)

[Etkin Komut Dosyası Hata Ayıklamaya Genel Bakış](../winscript/active-script-debugging-overview.md)

[Etkin Komut Dosyası Profil Oluşturmaya Genel Bakış](../winscript/active-script-profiling-overview.md)

[Windows Betik Arabirimleri Başvurusu](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Windows betiği arka planı

Windows komut dosyası arabirimleri iki kategoriye ayrılır: Windows komut dosyası konakları ve Windows komut dosyası motorları. Bir ana bilgisayar, betikleri çalıştırmak için altyapıda bir betik altyapısı ve çağrılar oluşturur. Windows komut dosyası ana bilgisayarlarının örnekleri şunlardır:

- Microsoft Internet Explorer

- Internet yazma araçları

- Kabuk

Windows komut dosyası motorları, aşağıdakiler de dahil olmak üzere herhangi bir dil veya çalışma zamanı ortamı için geliştirilebilir:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lisp

Konağın uygulanmasını mümkün olduğunca esnek hale getirmek için Windows betiği için bir OLE Otomasyon sarmalayıcısı sağlanır. Ancak, komut dosyası altyapısını oluşturmak için bu sarmalayıcı nesnesini kullanan bir ana bilgisayar, çalışma zamanı ad alanı, Kalıcılık modeli vb. üzerinde denetim derecesine sahip değildir ve bu, Windows betiğini doğrudan kullanacaksa olur.

Windows komut dosyası tasarımı, yazma ortamında gerekli olan arabirim öğelerini (örneğin, tarayıcılar ve görüntüleyiciler) ve komut dosyası altyapılarını (örneğin, VBScript) hafif tutulabilirler.

## <a name="windows-script-basic-architecture"></a>Windows betiği temel mimarisi

Aşağıdaki çizimde bir Windows betik sistemi ve bir Windows betik altyapısı arasındaki etkileşim gösterilmektedir.

Ana bilgisayar ve altyapı arasındaki etkileşime dahil olan adımlar aşağıdaki listede verilmiştir.

1. Bir proje oluşturun. Konak bir proje veya belge yükler. (Bu adım Windows betiğine özgü değildir, ancak bu, tamamlanma açısından burada yer alır.)

2. Windows komut dosyası altyapısını oluşturun. Ana bilgisayar `CoCreateInstance` , kullanılacak özel betik altyapısının sınıf tanımlayıcısını (CLSID) belirterek yeni bir Windows komut dosyası altyapısı oluşturmak için çağırır. Örneğin, Internet Explorer 'ın HTML tarayıcısı, komut dosyası altyapısının sınıf tanımlayıcısını HTML etiketinin CLSID = özniteliği aracılığıyla alır \<OBJECT> .

3. Betiği yükleyin. Betik içeriği kalıcı hale getirildi, ana bilgisayar komut dosyası `IPersist*::Load` depolama, akış veya özellik çantasına akışa almak için betik altyapısı yöntemini çağırır. Aksi halde, ana bilgisayar `IPersist*::InitNew` bir null betik oluşturmak için veya [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) yöntemini kullanır. Betiği metin olarak tutan bir ana bilgisayar, [IActiveScriptParse::P arseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) kullanarak komut dosyası altyapısını, çağrıldıktan sonra betiğin metnini akışa alabilir `IActiveScriptParse::InitNew` .

4. Adlandırılmış öğeleri ekleyin. Betik altyapısının ad alanına içeri aktarılan her üst düzey adlandırılmış öğe (örneğin, sayfalar ve formlar) için, konak altyapının ad alanında bir giriş oluşturmak için [IActiveScript:: Addnamedidıtem](../winscript/reference/iactivescript-addnameditem.md) yöntemini çağırır. En üst düzey adlandırılmış öğeler zaten 3. adımda yüklenen betiğin kalıcı durumunun parçasıysa bu adım gerekli değildir. Ana bilgisayar `IActiveScript::AddNamedItem` alt düzey adlandırılmış öğeler (örneğin, BIR HTML sayfasına denetimler) eklemek için kullanmaz; bunun yerine, altyapı, ana bilgisayar ve arabirimlerini kullanarak en üst düzey öğelerden alt düzey öğeleri dolaylı olarak alır `ITypeInfo` `IDispatch` .

5. Betiği çalıştırın. Ana bilgisayar, [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) yönteminde SCRIPTSTATE_CONNECTED bayrağını ayarlayarak altyapının betiği çalıştırmaya başlamasını sağlar. Bu çağrı, statik bağlama dahil olmak üzere herhangi bir betik altyapısı oluşturma işini, olaylara (aşağıya bakın) çağrı yapmayı ve kodu bir komut dosyası oluşturma işlevine benzer bir şekilde yürütmeyi sağlar `main()` .

6. Öğe bilgilerini al. Betik altyapısının bir simgeyi en üst düzey öğeyle ilişkilendirmesi gerektiğinde, verilen öğe hakkında bilgi döndüren [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemini çağırır.

7. Olayları bağlama. Asıl betiği başlatmadan önce, komut dosyası altyapısı arabirim aracılığıyla tüm ilgili nesnelerin olaylarına bağlanır `IConnectionPoint` .

8. Özellikleri ve yöntemleri çağırın. Betik çalışırken, komut dosyası altyapısı, `IDispatch::Invoke` veya diğer standart ole bağlama mekanizmaları aracılığıyla adlandırılmış nesnelerdeki yöntemlere ve özelliklere başvuruları yeniden ayırır.

## <a name="windows-script-terms"></a>Windows komut dosyası terimleri

Bu liste, bu belgede kullanılan betiklerle ilgili terimlerin tanımlarını içerir.

|Terim|Tanım|
|----------|----------------|
|Kod nesnesi|Betik altyapısı tarafından oluşturulan, Visual Basic bir formun arkasındaki modül veya adlandırılmış bir öğeyle ilişkili C++ sınıfı gibi bir adlandırılmış öğeyle ilişkili bir örnek. Tercihen, ana bilgisayar veya diğer betik olmayan varlığın kod nesnesini işleyebilmesi için OLE Otomasyonu 'Nu destekleyen OLE bileşen nesne modeli (COM) nesnesidir.|
|Adlandırılmış öğe|Ana bilgisayarın betiğe ilgi çekici olduğunu bir OLE COM nesnesi (tercihen OLE Otomasyonu 'nu destekleyen). Örnek olarak, bir Web tarayıcısında HTML sayfası ve tarayıcı ile Microsoft Word 'deki belge ve Iletişim kutuları bulunur.|
|Komut Dosyası|Betik altyapısının çalıştırdığı programı oluşturan veriler. Bir betik, metin parçaları, blokları `pcode` veya hatta makineye özgü yürütülebilir bayt kodları dahil herhangi bir bitişik yürütülebilir veri olabilir. Bir ana bilgisayar, `IPersist*` arabirimleri veya [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) arabirimi aracılığıyla komut dosyası motoruna bir betik yükler.|
|Betik altyapısı|Komut dosyalarını işleyen OLE nesnesi. Bir betik altyapısı, [IActiveScript](../winscript/reference/iactivescript.md) ve isteğe bağlı olarak [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) arabirimlerini uygular.|
|Betik sistemi|Windows komut dosyası altyapısının sahibi olan uygulama veya program. Ana bilgisayar [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) ve isteğe bağlı olarak [ıactivescriptsitewindow](../winscript/reference/iactivescriptsitewindow.md) arabirimlerini uygular.|
|Kod oluşturma yöntemi|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) arabirimi aracılığıyla bir nesneye eklenen betiğin bir bölümü. Betikteki toplam koleksiyonu, betiğizin verir.|
|Betik dili|Bir betiğin yazıldığı dil (VBScript, örneğin) ve bu dilin semantiği.|