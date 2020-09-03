---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0214d3e8d097efa31b3f8b02e67f419226a093a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461345"
---
# <a name="idiasymbol"></a>IDiaSymbol
Bir sembol örneğinin özelliklerini açıklar.

## <a name="syntax"></a>Syntax

```
IDiaSymbol : IUnknown
```

## <a name="methods-in-alphabetical-order"></a>Alfabetik sırada Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaSymbol` .

> [!NOTE]
> Semboller, simgenin türüne bağlı olarak bu yöntemlerin yalnızca bazılarına anlamlı veriler döndürür. Bir Yöntem döndürüyorsa `S_OK` , bu yöntem anlamlı veri döndürdü.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Simgenin tüm alt öğelerini alır.|
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Simgenin alt öğelerini alır. Bu yöntem, [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)'ın genişletilmiş sürümüdür.|
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Simgenin belirli bir adreste geçerli olan alt öğelerini alır.|
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Simgenin, belirtilen göreli sanal adreste (RVA) geçerli olan alt öğelerini alır.|
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Simgenin belirtilen sanal adreste geçerli olan alt öğelerini alır.|
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Bir istemcinin belirli bir adresteki tüm satır içi çerçeveler üzerinde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Bir istemcinin belirtilen göreli sanal adreste (RVA) bulunan tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Bir istemcinin, Bu sembolde doğrudan veya dolaylı olarak, satır numarası bilgileri üzerinden yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Bir istemcinin, belirtilen adres aralığı içinde Bu sembolde bulunan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemek için bir sabit listesi alır.|
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Bir istemcinin, belirtilen göreli sanal adres (RVA) içindeki Bu sembolde yer alan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Bir istemcinin, belirtilen sanal adres (VA) içindeki Bu sembolde yer alan ve doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Karşılık gelen bir etiket değeri verildiğinde, bu yöntem, belirtilen bir göreli sanal adresteki bu saplama işlevinde bulunan simgelerin bir listesini döndürür.|
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|C++ AMP saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.|
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|C++ AMP Hızlandırıcı saplama işlevine karşılık gelen tüm Hızlandırıcı işaretçisi etiketi değerlerini döndürür.|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Bir sınıf üyesinin erişim değiştiricisini alır.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Bir adres konumunun konum kısmını alır.|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Bir adres konumunun bölüm kısmını alır.|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Başka bir simgenin bu adrese başvurmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Program veritabanının yaş değerini alır.|
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Dizi dizin türünün sembol tanımlayıcısını alır.|
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Simgenin dizi dizin türü tanımlayıcısını alır.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Arka uç ana sürüm numarasını alır.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Arka uç ikincil sürüm numarasını alır.|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Arka uç derleme numarasını alır.|
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Taban veri konumunu alır.|
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Temel veri yuvasını alır.|
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|İşaretçinin dayandığı simgeyi alır.|
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|İşaretçinin dayandığı sembol KIMLIĞINI alır.|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Basit bir türün tür etiketini alır.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Bir konumun bit konumunu alır.|
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|HLSL türünün yerleşik türünü alır.|
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Metodun çağırma kuralının bir göstergesini döndürür.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Simgenin sınıf üst öğesine bir başvuru alır.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Simgenin sınıf üst tanımlayıcısını alır.|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Simgenin bir kod adresine başvuruda bulunup bulunmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Simgenin derleyicinin oluşturulup oluşturulmayacağını belirten bir bayrak alır.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|[Compiland](../../debugger/debug-interface-access/compiland.md)oluşturmak için kullanılan derleyicinin adını alır.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Kullanıcı tanımlı veri türünün bir oluşturucuya sahip olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Bu sembolün içeren sembolünü alır.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Kullanıcı tanımlı veri türünün sabit olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Bir liste veya dizideki öğelerin sayısını alır.|
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Yerel sembolüyle ilişkili geçerli adres aralıklarının sayısını alır.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|İşlevin özel bir çağırma kuralı kullanıp kullanmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Bir OEM sembolünün veri baytlarını alır.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Bir veri sembolünün değişken sınıflandırmasını alır.|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Derlenen programın veya birimin Düzenle ve devam et özelliklerini açıklayan bayrağı alır.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|İşlevin bir en fazla dönüş kullanıp kullanmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Ön uç ana sürüm numarasını alır.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Ön uç ikincil sürüm numarasını alır.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Ön uç derleme numarasını alır.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Ortak sembolün bir işleve başvurduğunu belirten bir bayrak alır.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Simgenin GUID 'INI alır.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|İşlevin çağrısı içerip içermediğini gösteren bir bayrak alır `alloca` .|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Kullanıcı tanımlı veri türünde tanımlanmış atama işleçleri olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Kullanıcı tanımlı veri türünde tanımlanmış herhangi bir atama işleci olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Compiland 'ın herhangi bir hata ayıklama bilgisi içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|İşlevin C++ stili özel durum işleyicisine sahip olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|İşlevin zaman uyumsuz özel durum işleyicisine sahip olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|İşlevin satır içi derleme içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|İşlevin longjmp komutu içerip içermediğini belirten bir bayrak alır (C stili özel durum işlemenin parçası).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Modülün yönetilen kod içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Kullanıcı tanımlı veri türünün iç içe geçmiş tür tanımlarına sahip olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|İşlevin veya compiland 'ın ' de ( [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) derleyici anahtarı aracılığıyla) derlenmiş güvenlik denetimlerine sahip olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|İşlevin Win32 stili yapılandırılmış özel durum Işleme içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|İşlevin bir setjmp komutu içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Kullanıcı tanımlı veri türünün dolaylı bir sanal temel sınıf olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|İşlevin satır içi özniteliğiyle işaretlenip işaretlenmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|İşlevin kesme yönergesinden dönüş yapıp kullanmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|İşlevin temel sınıf sanal işlevi olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Simgenin bir C++ AMP Hızlandırıcısı için derlenmiş kodda bir grup paylaşılan yerel değişkenine karşılık geldiğini belirten bir bayrak alır.|
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Simgenin bir C++ AMP Hızlandırıcısı için derlenmiş koddaki bir işaretçi değişkeninin etiket bileşeni için *Açıklama aralığı simgesine* karşılık geldiğini belirten bir bayrak alır. Tanım aralığı simgesi, bir adres yayılımı için bir değişkenin konumudur.|
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Simgenin bir çağrıya karşılık gelen hızlandırıcı için derlenen bir gölgelendirici için üst düzey işlev simgesine karşılık geldiğini gösterir `parallel_for_each` .|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Verilerin birçok sembol toplamasının bir parçası olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Sembol dosyasının C türlerini içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Modülün ortak ara dil (CıL) ile yerel koda dönüştürülüp dönüştürülmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Kullanıcı tanımlı veri türü öğelerinin belirli bir sınıra hizalanıp Hizalanmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Bu sembolün yüksek düzey gölgelendirici dili (HLSL) verilerini temsil edip etmediğini belirtir.|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Modülün [/hotpatch (düzeltme eki uygulanmış görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarı ile derlendiğini belirten bir bayrak alır.|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Managed compiland 'in bağlayıcının LTCG ile bağlantılı olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Matrisin satır birincil olup olmadığını belirtir.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Managed compiland 'ın bir. netmodule olup olmadığını belirten bir bayrak alır (yalnızca meta veriler içerir).|
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|`this`İşaretçinin birden çok devralmayla bir veri üyesine işaret ettiğini belirtir.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|İşlevin [çıplak](/cpp/cpp/naked-cpp) özniteliğe sahip olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Değişkenin en iyi duruma getirilip getirilmediğini belirtir.|
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|`this`İşaretçinin bir sembol değerini temel alarak çalışıp çalışmadığını belirtir.|
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Bu sembolün bir veri üyesine yönelik bir işaretçi olup olmadığını belirtir.|
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Bu sembolün bir üye işlevine yönelik bir işaretçi olup olmadığını belirtir.|
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Değişkenin bir dönüş değeri içerip içermediğini belirtir.|
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Modülün/SDL seçeneğiyle derlenip derlenmediğini belirtir.|
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|`this`İşaretçinin tek devralma ile bir veri üyesine işaret ettiğini belirtir.|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Verilerin ayrı sembollerin toplamına bölünmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Bir işlev veya dönüştürücü katmanının statik olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Özel simgelerin sembol dosyasından bırakılıp nakledilmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|`this`İşaretçinin sanal devralmayla bir veri üyesine işaret ettiğini belirtir.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Kaynağın dilini alır.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Bu sembol tarafından temsil edilen nesne tarafından kullanılan bellek bayt sayısını alır.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Simgenin sözcük üst öğesi için bir başvuru alır.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Simgenin sözcük üst tanımlayıcısını alır.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Nesnenin yüklendiği kitaplığın veya nesne dosyasının dosya adını alır.|
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Yerel simgenin geçerli olduğu adres aralığının uzunluğunu döndürür.|
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Yerel sembolün geçerli olduğu başlangıç adresi aralığının bölüm bölümünü döndürür.|
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Yerel sembolün geçerli olduğu başlangıç adresi aralığının konum parçasını döndürür.|
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Yerel simgenin geçerli olduğu adres aralığının başlangıcını döndürür.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Bir veri sembolünün konum türünü alır.|
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Bir FORTRAN dizi boyutunun alt sınırını alır.|
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Bir FORTRAN dizi boyutunun alt sınırının sembol tanımlayıcısını alır.|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Hedef CPU 'nun türünü alır.|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Simgenin yönetilen koda işaret edilip edilmeyeceğini belirten bir bayrak alır.|
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Bellek alanı türünü alır.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Simgenin Microsoft ara dili (MSIL) koduna işaret edilip edilmeyeceğini belirten bir bayrak alır.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Simgenin adını alır.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Kullanıcı tanımlı veri türünün iç içe olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|İşlevin [noinline](/cpp/cpp/noinline) özniteliğiyle işaretlenip işaretlenmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|İşlevin [noreturn](/cpp/cpp/noreturn) özniteliğiyle bildirilip aşılmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Yığın arabelleği denetiminin bir parçası olarak yığın sıralaması yapılıp yapılmayacağını belirten bir bayrak alır.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|İşlevin veya etiketin hiç erişilmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|C++ AMP saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.|
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Özgün türe uygulanan değiştiricilerin sayısını alır.|
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Kayıt dizinlerinin sayısını alır.|
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Matristeki satır sayısını alır.|
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Matristeki sütun sayısını alır.|
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Nesne dosyası adını alır.|
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Bir sınıf yöntemi için nesne işaretçisinin türünü alır.|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Simgenin `oemId` değerini alır.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Simgenin `oemSymbolId` değerini alır.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Sembol konumunun sapmasını alır.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|İşlevin veya etiketin, iyileştirilmiş kod ve hata ayıklama bilgileri içerip içermediğini gösteren bir bayrak alır.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Kullanıcı tanımlı veri türünün aşırı yüklenmiş işleçlere sahip olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Kullanıcı tanımlı veri türünün paketlenip paketlenmediğini belirten bir bayrak alır.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Program veya compiland 'in derlendiği Platform türünü alır.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|İşlevin saf sanal olup olmadığını gösteren bir bayrak alır.|
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Bir FORTRAN çok boyutlu dizisinin derecesini alır.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|İşaretçi türünün bir başvuru olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Konumun kayıt göstergesini alır.|
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Kayıt türünü alır.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Konumun göreli sanal adresini (RVA) alır.|
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|`this`İşaretçinin kısıtlı olarak işaretlenip işaretlenmediğini belirtir.|
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Örnekleyici yuvasını alır.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Kullanıcı tanımlı veri türünün global olmayan bir sözcük temelli kapsamda görüntülenip görüntülenmeyeceğini belirten bir bayrak alır.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Simgenin imza değerini alır.|
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Kullanıcı tanımlı bir türün bir üyesinin boyutunu alır.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Konumun yuva numarasını alır.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Kaynak dosyanın dosya adını alır.|
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Belirtilen kullanıcı tanımlı türün nerede tanımlandığını belirten kaynak dosya ve satır numarasını alır.|
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Matrisin ilerini alır veya bir dizi harcar.|
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Alt türü alır.|
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Alt tür KIMLIĞINI alır.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Simgelerin yüklendiği dosyanın adını alır.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Benzersiz sembol tanımlayıcısını alır.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Sembol türü sınıflandırıcısını alır.|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Bir dönüştürücü hedefinin konum bölümünü alır.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Bir dönüştürücü hedefinin göreli sanal adresini (RVA) alır.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Bir dönüştürücü hedefinin adres bölümünü alır.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Bir dönüştürücü hedefinin sanal adresini (VA) alır.|
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Doku yuvasını alır.|
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`this`Yöntemi için mantıksal ayarlanıcısı alır.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Bir işlevin dönüştürücü türünü alır.|
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Temel alınan yürütülebilir dosyanın zaman damgasını alır.|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Yönetilen bir işlevin veya değişkenin meta veri belirtecini alır.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|İşlev imzasına bir başvuru alır.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Simgenin tür tanımlayıcısını alır.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Bu simge için derleyiciye özgü tür değerlerinin dizisini alır.|
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini alır.|
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Uıav yuvasını alır.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Kullanıcı tanımlı bir tür (UDT) alır.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Kullanıcı tanımlı veri türünün hizalanmamış olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|C++ ile düzenlenmiş veya bağlantı adı için, açıklanmamalıdır adı alır.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`get_undecoratedName`Uzantı alanının değerine göre, açıklanedilmemiş adı alan metodun uzantısı.|
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Özgün (değiştirilmemiş) türün KIMLIĞINI alır.|
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Bir FORTRAN dizi boyutunun üst sınırını alır.|
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Bir FORTRAN dizi boyutunun üst sınırının sembol tanımlayıcısını alır.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Bir sabitin değerini alır.|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|İşlevin sanal olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Konumun sanal adresini (VA) alır.|
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Kullanıcı tanımlı veri türünün bir sanal temel sınıf olup olmadığını belirten bir bayrak alır.|
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Dizini sanal taban öteleme tablosuna alır.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Sanal bir işlevin sanal işlev tablosundaki sapmayı alır.|
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Sanal Taban işaretçisinin konumunu alır.|
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Bir sanal temel tablo işaretçisinin türünü alır.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Kullanıcı tanımlı bir tür için sanal tablo türünün sembol arabirimini alır.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Simgenin sanal tablo şekli tanımlayıcısını alır.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Kullanıcı tanımlı veri türünün geçici olup olmadığını belirten bir bayrak alır.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Aşağıdaki yöntemlerden birini çağırarak bu arabirimi edinin:

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
Bu örnek, belirli bir göreli sanal adreste bir işlev için yerel değişkenlerin nasıl görüntüleneceğini gösterir. Ayrıca farklı türlerin simgelerinin birbirleriyle nasıl ilişkili olduğunu gösterir.

> [!NOTE]
> `CDiaBSTR` , `BSTR` örnekleme kapsam dışına geçtiğinde bir ve otomatik olarak dizeyi serbest bırakma olarak işleyen bir sınıftır.

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
`Header:` Dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Compiland](../../debugger/debug-interface-access/compiland.md)
