---
description: Sembol örneğinin özelliklerini açıklar.
title: IDiaSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 99b0fdd7526a9d14b8f5d0f937b63c5303c3ace2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121268"
---
# <a name="idiasymbol"></a>IDiaSymbol
Sembol örneğinin özelliklerini açıklar.

## <a name="syntax"></a>Syntax

```
IDiaSymbol : IUnknown
```

## <a name="methods-in-alphabetical-order"></a>Alfabetik Sırada Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaSymbol` gösterir.

> [!NOTE]
> Semboller, sembol türüne bağlı olarak bu yöntemlerden yalnızca bazıları için anlamlı veriler dönecektir. Bir yöntem `S_OK` döndürürse, bu yöntem anlamlı veriler döndürdü.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Sembolün tüm çocuklarını alın.|
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Sembolün children'larını alın. Bu yöntem [IDiaSymbol::findChildren'ın genişletilmiş sürümüdür.](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Belirtilen adreste geçerli olan sembole sahip olan çocuklarına sahip olur.|
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Belirtilen bir göreli sanal adreste (RVA) geçerli olan sembolün çocuklarını alır.|
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Belirtilen sanal adreste geçerli olan sembole sahip olan çocuklarına sahip olur.|
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|bir istemcinin belirli bir adresteki tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit adı verir.|
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Bir istemcinin belirtilen bir göreli sanal adresteki (RVA) tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit değer alır.|
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler üzerinde devamını sağlayan bir sabit değer alır.|
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Bir istemcinin satır içinde, doğrudan veya dolaylı olarak bu sembolde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırıcısını verir.|
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Bir istemcinin, belirtilen adres aralığındaki bu sembolde satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırıcısını verir.|
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Bir istemcinin, belirtilen göreli sanal adres (RVA) içindeki bu simgede satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırarak alır.|
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Bir istemcinin, belirtilen sanal adres (VA) içindeki bu simgede satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak devamını sağlayan bir numaralama alır.|
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste bu saplama işlevinde yer alan sembollerin bir numaralama döndürür.|
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Bir saplama işlevinde hızlandırıcı işaretçisi C++ AMP döndürür.|
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Bir hızlandırıcı saplama işlevine karşılık gelen tüm hızlandırıcı işaretçisi C++ AMP değerlerini döndürür.|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Bir sınıf üyesinin erişim değiştiricisini alın.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Adres konumunun uzaklık bölümünü alın.|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Adres konumunun bölüm bölümünü alan.|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Başka bir sembolün bu adrese başvurıp başvurul olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Program veritabanının yaş değerini alır.|
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Dizi dizini türünün sembol tanımlayıcısını verir.|
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Sembolün dizi dizin türü tanımlayıcısını döndürür.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Arka uç ana sürüm numarasını alın.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Arka uç ikincil sürüm numarasını alın.|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Arka uç derleme numarasını alın.|
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Temel veri uzaklığını alınır.|
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Temel veri yuvasını alın.|
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|İşaretçinin temel alınarak simgeyi alan.|
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|İşaretçinin dayandır olduğu sembol kimliğini alın.|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Basit bir türün tür etiketini alın.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Bir konumun bit konumunu alın.|
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|HLSL türünün yerleşik bir türünü alın.|
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Bir yöntemin çağırma kuralına bir gösterge döndürür.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Sembolün sınıf üst öğesi için bir başvuru verir.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Sembolün sınıf üst tanımlayıcısını verir.|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Sembolün bir kod adresine başvurduğuna işaret eden bir bayrak alınır.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Sembolün derleyici tarafından oluşturulıp oluşturulmadı olduğunu belirten bir bayrak alınır.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Compiland oluşturmak için kullanılan [derleyicinin adını alın.](../../debugger/debug-interface-access/compiland.md)|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Kullanıcı tanımlı veri türünün oluşturucusu olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Bu sembolün içeren sembolünü alın.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Kullanıcı tanımlı veri türünün sabit olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Bir liste veya dizideki öğe sayısını döndürür.|
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Yerel simgeyle ilişkili geçerli adres aralıklarının sayısını alın.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|İşlevin özel bir çağırma kuralı kullandığını belirten bir bayrak verir.|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|OEM simgesinin veri baytlarını alan.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Bir veri simgesinin değişken sınıflandırmasını alan.|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Derlenmiş programın veya birimin Düzenle ve Devam Ediyor özelliklerini açıklayan bayrağını alın.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|İşlevin uzak bir dönüş kullandığına işaret eden bir bayrak verir.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Ön uç ana sürüm numarasını alın.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Ön uç ikincil sürüm numarasını alın.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Ön uç derleme numarasını alın.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Ortak sembolün bir işleve başvurduğuna işaret eden bir bayrak verir.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Sembolün GUID'lerini alın.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|İşlevin çağrısı içerdiğini belirten bir bayrak `alloca` verir.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Kullanıcı tanımlı veri türünün tanımlanmış atama işleçleri olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Kullanıcı tanımlı veri türünün tanımlanmış herhangi bir türe sahip olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Derlemenin herhangi bir hata ayıklama bilgisi içerdiğini belirten bir bayrak alınır.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|İşlevin C++stili bir özel durum işleyicisi olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|İşlevin zaman uyumsuz bir özel durum işleyicisi olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|İşlevin satır içi derlemesi olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|İşlevin longjmp komutu (C stili özel durum işlemenin bir parçası) içerdiğini belirten bir bayrak alır.|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Modülde yönetilen kod olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Kullanıcı tanımlı veri türünün iç içe geçmiş tür tanımları olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|İşlevin veya derlemenin içinde [(/GS (Arabellek](/cpp/build/reference/gs-buffer-security-check) Güvenlik Denetimi) derleyici anahtarı aracılığıyla) derlenmiş güvenlik denetimleri olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|İşlevin Win32 stilinde Yapılandırılmış Özel Durum İşleme'ye sahip olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|İşlevin bir setjmp komutu içerdiğini belirten bir bayrak verir.|
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Kullanıcı tanımlı veri türünün dolaylı bir sanal temel sınıf olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|İşlevin satır içi özniteliğiyle işaretlenmiş olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|İşlevin kesme yönergesi dönüşe sahip olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|İşlevin temel sınıf sanal işlevi olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Sembolün, C++ AMP Accelerator için derlenmiş kodda grup tarafından paylaşılan yerel değişkene karşılık gelen bir bayrağını alın.|
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Sembolün, C++ AMP Accelerator için derlenmiş  kodda bir işaretçi değişkeninin etiket bileşeni için tanım aralığı simgesine karşılık gelen bir bayrak alınır. Tanım aralığı simgesi, bir adres aralığı için değişkenin konumudür.|
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Sembolün, bir çağrıya karşılık gelen bir hızlandırıcı için derlenmiş gölgelendirici için üst düzey işlev simgesine karşılık gelen bir simge olup olmadığını `parallel_for_each` gösterir.|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Verilerin çok sayıda simgenin bir toplama parçası olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Sembol dosyasının C türleri içerdiğini belirten bir bayrak alınır.|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Modülün Ortak Ara Dilden (CIL) yerel koda dönüştürülerek dönüştürülerek dönüştürülenin olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Kullanıcı tanımlı bir veri türünün öğelerinin belirli bir sınıra hizalanmış olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Bu sembolün Üst Düzey Gölgelendirici Dili (HLSL) verilerini temsil edip ettiğini belirtir.|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Modülün [/hotpatch (Hotpatchable Image Oluştur)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarıyla derlenmiş olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Yönetilen derlemenin, bağlantıcının LTCG'si ile bağlantılı olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Matrisin satır ana dalı olup olmadığını belirtir.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Yönetilen derlemenin bir .netmodule (yalnızca meta veriler içeren) olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|İşaretçinin birden `this` çok devralmaya sahip bir veri üyesine işaret edip ede olmadığını belirtir.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|İşlevin çıplak özniteliğine sahip olup olmadığını belirten bir [bayrak](/cpp/cpp/naked-cpp) verir.|
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Değişkenin iyileştirilmiş olup olmadığını belirtir.|
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|İşaretçinin `this` bir sembol değerini temel alarak olup olmadığını belirtir.|
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Bu sembolün bir veri üyesinin işaretçisi olup olmadığını belirtir.|
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Bu sembolün üye işlevinin işaretçisi olup olmadığını belirtir.|
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Değişkenin bir dönüş değeri taşıdığını belirtir.|
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Modülün /SDL seçeneğiyle derlenmiş olup olmadığını belirtir.|
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|İşaretçinin tek `this` devralma ile bir veri üyesine işaret edip ede olmadığını belirtir.|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Verilerin ayrı sembollerin bir araya toplanmış olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Bir işlevin veya thunk katmanının statik olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Özel sembollerin sembol dosyasından çıkarılmış olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|İşaretçinin sanal `this` devralma ile bir veri üyesine işaret edip ede olmadığını belirtir.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Kaynağın dilini alan.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Bu simgeyle temsil edilen nesne tarafından kullanılan bellek bayt sayısını alın.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Sembolün sözcük üst öğesi için bir başvuru verir.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Sembolün sözcüksel üst tanımlayıcısını verir.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Nesnenin yükleniyor olduğu kitaplığın veya nesne dosyasının dosya adını alın.|
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Yerel sembolün geçerli olduğu adres aralığının uzunluğunu döndürür.|
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Yerel sembolün geçerli olduğu başlangıç adres aralığının bölüm bölümünü döndürür.|
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Başlangıç adres aralığının yerel sembolün geçerli olduğu kaydırma bölümünü döndürür.|
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Yerel sembolün geçerli olduğu adres aralığının başlangıcını döndürür.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Bir veri simgesinin konum türünü alan.|
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|FORTRAN dizisi boyutunun alt sınırlarını döndürür.|
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|ForTRAN dizisi boyutunun alt sınırlarının sembol tanımlayıcısını verir.|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Hedef CPU'nun türünü alın.|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Sembolün yönetilen koda başvurduğuna işaret eden bir bayrak alınır.|
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Bellek alanı türlerini alan.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Sembolün Microsoft Ara Dil (MSIL) koduna başvurup başvura olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Sembolün adını alan.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Kullanıcı tanımlı veri türünün iç içe geçmiş olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|İşlevin [noinline](/cpp/cpp/noinline) özniteliğiyle işaretlenmiş olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|işlevin [noreturn](/cpp/cpp/noreturn) özniteliğiyle bildir olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Yığın arabelleği denetimi kapsamında yığın sıralamanın yapılamayıp yapılmay olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|İşleve veya etikete hiçbir zaman ulaşılamay olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Bir saplama işlevinde hızlandırıcı işaretçisi C++ AMP döndürür.|
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Özgün türe uygulanan değiştiricilerin sayısını alın.|
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Kayıt dizinlerinin sayısını alın.|
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Matriste satır sayısını alan.|
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Matriste sütun sayısını alan.|
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Nesne dosya adını alın.|
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Bir sınıf yöntemi için nesne işaretçisinin türünü alın.|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Sembolün değerini `oemId` verir.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Sembolün değerini `oemSymbolId` verir.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Sembol konumunun uzaklığını alan.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|İşlevin veya etiketin hem iyileştirilmiş kod hem de hata ayıklama bilgileri içerdiğini belirten bir bayrak verir.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Kullanıcı tanımlı veri türünün aşırı yüklenmiş işleçlere sahip olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Kullanıcı tanımlı veri türünün paketli olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Programın veya derlemenin derlenmiş olduğu platform türünü alın.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|İşlevin saf sanal olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|FORTRAN çok boyutlu dizisinin derecesini alır.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|İşaretçi türünün başvuru olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Konumun yazmaç tasarımını alın.|
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Yazmaz türünü alın.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Konumun göreli sanal adresini (RVA) alan.|
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|İşaretçinin `this` kısıtlanmış olarak işaretlenmiş olup olmadığını belirtir.|
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Örnekleyici yuvasını alın.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Kullanıcı tanımlı veri türünün küresel olmayan sözcüksel bir kapsamda görüntülendiğinden işaret eden bir bayrak alınır.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Sembolün imza değerini verir.|
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Kullanıcı tanımlı bir türün üyesinin boyutunu alan.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Konumun yuva numarasını alan.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Kaynak dosyanın dosya adını alın.|
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Belirtilen kullanıcı tanımlı türün tanımlandığı yeri belirten kaynak dosyayı ve satır numarasını alın.|
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Matrisin veya strided dizisinin adımlarını döndürür.|
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Alt türü alınır.|
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Alt tür kimliğini alın.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Sembollerin yükleniyor olduğu dosyanın adını alın.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Benzersiz sembol tanımlayıcısını verir.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Sembol türü sınıflandırıcısını alın.|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Bir thunk hedefinin uzaklık bölümünü alan.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Bir thunk hedefinin göreli sanal adresini (RVA) alan.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Bir thunk hedefinin adres bölümünü alan.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Bir thunk hedefinin sanal adresini (VA) alan.|
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Doku yuvasını alan.|
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|yöntemi için `this` mantıksal ayarıcıyı alın.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Bir işlevin thunk türünü verir.|
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Temel alınan yürütülebilir dosyanın zaman damgasını alın.|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Yönetilen bir işlevin veya değişkenin meta veri belirteci alır.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|İşlev imzasını başvurur.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Sembolün tür tanımlayıcısını verir.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Bu sembol için derleyiciye özgü tür değerleri dizisinin alınır.|
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini döndürür.|
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Uav yuvasını alın.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Kullanıcı tanımlı türün (UDT) çeşitliliğini alır.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Kullanıcı tanımlı veri türünün hizasız olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|C++ ile dekore edilmiş veya bağlantı olan bir ad için düzeltilmez adı alınır.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Bir uzantı `get_undecoratedName` alanı değerine göre düzeltlanmamış adı alan yönteminin uzantısı.|
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Özgün (değiştirilmemiş) türün kimliğini alın.|
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|FORTRAN dizisi boyutunun üst sınırlarını döndürür.|
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|FORTRAN dizisi boyutunun üst sınırlarının sembol tanımlayıcısını verir.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Sabitin değerini verir.|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|İşlevin sanal olup olmadığını belirten bir bayrak verir.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Konumun sanal adresini (VA) alın.|
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Kullanıcı tanımlı veri türünün bir sanal temel sınıf olup olmadığını belirten bir bayrak alınır.|
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Dizini sanal temel yer değiştirme tablosuna alır.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Bir sanal işlevin sanal işlev tablosunda uzaklığı alır.|
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Sanal temel işaretçinin uzaklığını alan.|
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Sanal temel tablo işaretçisinin türünü alır.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Kullanıcı tanımlı bir tür için sanal tablo türünün sembol arabirimini alır.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Sembolün sanal tablo şekil tanımlayıcısını alır.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Kullanıcı tanımlı veri türünün geçici olup olmadığını belirten bir bayrak alınır.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Aşağıdaki yöntemlerden birini çağırarak bu arabirimi alın:

- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)

- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)

- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)

- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)

- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)

- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)

- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)

- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)

- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)

## <a name="example"></a>Örnek
Bu örnekte, belirli bir göreli sanal adreste bir işlev için yerel değişkenlerin nasıl görüntüleniyor olduğu gösterilir. Ayrıca farklı tür simgelerinin birbirine nasıl bağlı olduğunu gösterir.

> [!NOTE]
> `CDiaBSTR` , bir sarmalama ve örnekleme kapsam dışında olduğunda dize serbest serbest bırakarak otomatik `BSTR` olarak tanıtıcı bir sınıftır.

```C++
void DumpLocalVars( DWORD rva, IDiaSession *pSession )
{
    CComPtr< IDiaSymbol > pBlock;
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )
    {
        Fatal( "Failed to find symbols by RVA" );
    }
    CComPtr< IDiaSymbol > pscope;
    for ( ; pBlock != NULL; )
    {
        CComPtr< IDiaEnumSymbols > pEnum;
        // local data search
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )
        {
            Fatal( "Local scope findChildren failed" );
        }
        CComPtr< IDiaSymbol > pSymbol;
        DWORD tag;
        DWORD celt;
        while ( pEnum != NULL &&
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1)
        {
            pSymbol->get_symTag( &tag );
            if ( tag == SymTagData )
            {
                CDiaBSTR name;
                DWORD    kind;
                pSymbol->get_name( &name );
                pSymbol->get_dataKind( &kind );
                if ( name != NULL )
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );
            }
            else if ( tag == SymTagAnnotation )
            {
                CComPtr< IDiaEnumSymbols > pValues;
                // local data search
                wprintf_s( L"\tAnnotation:\n" );
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )
                    Fatal( "Annotation findChildren failed" );
                pSymbol = NULL;
                while ( pValues != NULL &&
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&
                        celt == 1 )
                {
                    CComVariant value;
                    if ( pSymbol->get_value( &value ) != S_OK )
                        Fatal( "No value for annotation data." );
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );
                    pSymbol = NULL;
                }
            }
            pSymbol = NULL;
        }
        pBlock->get_symTag( &tag );
        if ( tag == SymTagFunction )    // stop when at function scope
            break;
        // move to lexical parent
        CComPtr< IDiaSymbol > pParent;
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )
            && pParent != NULL ) {
            pBlock = pParent;
        }
        else
        {
            Fatal( "Finding lexical parent failed." );
        }
    };
}
```

## <a name="requirements"></a>Gereksinimler
`Header:` Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Compiland](../../debugger/debug-interface-access/compiland.md)
