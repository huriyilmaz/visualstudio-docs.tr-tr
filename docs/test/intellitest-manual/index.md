---
title: IntelliTest Başvuru Kılavuzu | Microsoft Geliştirici Test Araçları
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b1c40412da096db63da87e04711cdc1a95b5cc84
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "75591625"
---
# <a name="intellitest-reference-manual"></a>IntelliTest Başvuru Kılavuzu

## <a name="contents"></a>İçindekiler

* **[IntelliTest’e genel bakış](introduction.md)**
  - [IntelliTest’in kullanıma sunulması](introduction.md#the-hello-world-of-intellitest)
  - [Sınırlamalar](introduction.md#limitations)
    * [Belirleyici olmama](introduction.md#nondeterminism)
    * [Eşzamanlılık](introduction.md#concurrency)
    * [Yerel kod](introduction.md#native-code)
    * [Platform](introduction.md#platform)
    * [Dil](introduction.md#language)
    * [Sembolik akıl yürütme](introduction.md#symbolic-reasoning)
    * [Hatalı yığın izlemeleri](introduction.md#incorrect-stack-traces)
  - [Daha fazla bilgi](introduction.md#further-reading)

* **[IntelliTest’i kullanmaya başlama](getting-started.md)**
  - [Önemli öznitelikler](getting-started.md#important-attributes)
  - [Önemli statik yardımcı sınıfları](getting-started.md#helper-classes)

* **[Test Oluşturma](test-generation.md)**
  - [Test oluşturucuları](test-generation.md#test-generators)
  - [Parametreli birim testi](test-generation.md#parameterized-unit-testing)
  - [Genel parametreli birim testi](test-generation.md#generic-parameterized)
  - [Özel durumlara izin verme](test-generation.md#allowing-exceptions)
  - [İç türleri test etme](test-generation.md#internal-types)
  - [Varsayımlar ve onaylamalar](test-generation.md#assumptions-and-assertions)
  - [Ön koşul](test-generation.md#precondition)
  - [Son koşul](test-generation.md#postcondition)
  - [Test hataları](test-generation.md#test-failures)
  - [Kurulum ve kapatma](test-generation.md#setup-teardown)
  - [Daha fazla bilgi](test-generation.md#further-reading)

* **[Giriş Oluşturma](input-generation.md)**
  - [Kısıtlama çözücü](input-generation.md#constraint-solver)
  - [Dinamik kod kapsamı](input-generation.md#dynamic-code-coverage)
  - [Tamsayılar ve kayan noktalı sayılar](input-generation.md#integers-and-floats)
  - [Nesneler](input-generation.md#objects)
  - [Mevcut sınıflardan örnek oluşturma](input-generation.md#existing-classes)
  - [Görünürlük](input-generation.md#visibility)
  - [Parametreli sahte nesneler](input-generation.md#parameterized-mocks)
  - [Yapılar](input-generation.md#structs)
  - [Diziler ve dizeler](input-generation.md#arrays-and-strings)
  - [Ek giriş alma](input-generation.md#additional-inputs)
  - [Daha fazla bilgi](input-generation.md#further-reading)

* **[Keşif Sınırları](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Öznitelik Sözlüğü](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Ayarlar Şelalesi](settings-waterfall.md)**

* **[Statik Yardımcı Sınıflar](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Uyarılar ve Hatalar](warnings-and-errors.md)**
  - [MaxBranches aşıldı](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime aşıldı](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions aşıldı](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls aşıldı](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack aşıldı](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns aşıldı](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests aşıldı](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Çözüm somutlaştırılamıyor](warnings-and-errors.md#cannot-concretize-solution)
  - [Nesne oluşturmak için yardım gerekiyor](warnings-and-errors.md#help-construct)
  - [Türleri bulmak için yardım gerekiyor](warnings-and-errors.md#help-types)
  - [Kullanılabilir tür tahmin edildi](warnings-and-errors.md#usable-type-guessed)
  - [Araştırma sırasında beklenmeyen hata oluştu](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [İzlenmeyen metot çağrıldı](warnings-and-errors.md#uninstrumented-method-called)
  - [Dış metot çağrıldı](warnings-and-errors.md#external-method-called)
  - [İzlenmeyen metot çağrıldı](warnings-and-errors.md#uninstrumentable-method-called)
  - [Test edilebilirlik sorunu](warnings-and-errors.md#testability-issue)
  - [Sınırlama](warnings-and-errors.md#limitation)
  - [Çağrı uyuşmazlığı gözlemlendi](warnings-and-errors.md#observed-call-mismatch)
  - [Değer statik alanda depolandı](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
