---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8a71b6d406b7507930a5d1a7ce593a296220d5a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278652"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API başvuru

Bu konu, ad alanının `Microsoft::VisualStudio::CppUnitTestFramework` ortak üyelerini listeler. Microsoft Yerel Birim Test Çerçevesi'ni temel alan C++ birim testleri yazmak için bu API'leri kullanın. Konunun sonunda bir [Kullanım Örneği](#example) vardır.

Üstbilgi ve lib dosyaları * \<Visual Studio yükleme klasörü altında>\VC\Auxiliary\VS\UnitTest*bulunur.

Üstbilgi ve lib yolları, Yerel Test projesinde otomatik olarak yapılandırılır.

## <a name="in-this-topic"></a><a name="In_this_topic"></a>Bu konuda

[CppUnitTest.h](#cppUnitTest_h)

- [Test sınıfları ve yöntemleri oluşturma](#create_test_classes_and_methods)

- [Başlatma ve temizleme](#Initialize_and_cleanup)

  - [Test yöntemleri](#test_methods)

  - [Test sınıfları](#test_classes)

  - [Test modülleri](#test_modules)

- [Test öznitelikleri oluşturma](#create_test_attributes)

  - [Test yöntemi öznitelikleri](#test_method_attributes)

  - [Sınıf özniteliklerini test edin](#test_class_attributes)

  - [Test modülü öznitelikleri](#test_module_attributes)

  - [Önceden tanımlanmış öznitelikler](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Genel İddialar](#general_asserts)

    - [Eşittir](#general_are_equal)

    - [Eşit Değildir](#general_are_not_equal)

    - [Aynı](#general_are_same)

    - [Aynı değildir](#general_are_not_same)

    - [Null mu](#general_is_null)

    - [Null değil mi](#general_is_not_null)

    - [Doğru mu](#general_is_True)

    - [Yanlış mı](#general_is_false)

    - [Başarısız](#general_Fail)

  - [Windows Runtime Asserts](#winrt_asserts)

    - [Eşittir](#winrt_are_equal)

    - [Aynı](#winrt_are_same)

    - [Eşit Değildir](#winrt_are_not_equal)

    - [Aynı değildir](#winrt_are_not_same)

    - [Null mu](#winrt_is_null)

    - [Null değil mi](#winrt_is_not_null)

  - [Özel Durum İddiaları](#exception_asserts)

    - [Özel Durum Beklentisi](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Günlükçü](#logger)

    - [Mesaj Yaz](#write_message)

  - [Kullanım Örneği](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a>CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a>Test sınıfları ve yöntemleri oluşturma

```cpp
TEST_CLASS(className)
```

Test yöntemleri içeren her sınıf için gereklidir. *className'yi* test sınıfı olarak tanımlar. `TEST_CLASS`ad-manzara kapsamında beyan edilmelidir.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

*MethodName'yi* bir test yöntemi olarak tanımlar. `TEST_METHOD`yöntemin sınıfı kapsamında bildirilmelidir.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a>Başlatma ve temizleme

#### <a name="test-methods"></a><a name="test_methods"></a>Test yöntemleri

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

*MethodName'yi* her test yöntemi çalıştırılmadan önce çalışan bir yöntem olarak tanımlar. `TEST_METHOD_INITIALIZE`bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfı kapsamında tanımlanmalıdır.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Her test yöntemi çalıştırılan sonra çalışan bir yöntem olarak *methodName* tanımlar. `TEST_METHOD_CLEANUP`bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfı kapsamında tanımlanmalıdır.

#### <a name="test-classes"></a><a name="test_classes"></a>Test sınıfları

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

*MethodName'yi* her test sınıfı oluşturulmadan önce çalışan bir yöntem olarak tanımlar. `TEST_CLASS_INITIALIZE`bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfı kapsamında tanımlanmalıdır.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

*MethodName'yi* her test sınıfı oluşturulduktan sonra çalışan bir yöntem olarak tanımlar. `TEST_CLASS_CLEANUP`bir test sınıfında yalnızca bir kez tanımlanabilir ve test sınıfı kapsamında tanımlanmalıdır.

#### <a name="test-modules"></a><a name="test_modules"></a>Test modülleri

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Modül yüklendiğinde çalışan *yöntem metoduName'yi* tanımlar. `TEST_MODULE_INITIALIZE`bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmesi gerekir.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Modül boşaltıldığında çalışan *yöntem metoduName'yi* tanımlar. `TEST_MODULE_CLEANUP`bir test modülünde yalnızca bir kez tanımlanabilir ve ad alanı kapsamında bildirilmesi gerekir.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a>Test öznitelikleri oluşturma

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a>Test yöntemi öznitelikleri

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Test yöntemi `TEST_METHOD_ATTRIBUTE` *testMethodName'e*bir veya daha fazla makro ile tanımlanan öznitelikleri ekler.

Makro `TEST_METHOD_ATTRIBUTE` adı *öznitelik Adı* ve değer *özniteliğiDeğer*ile bir öznitelik tanımlar.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a>Sınıf özniteliklerini test edin

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Test sınıfı `TEST_CLASS_ATTRIBUTE` *testClassName'ye*bir veya daha fazla makroyla tanımlanan öznitelikleri ekler.

Makro `TEST_CLASS_ATTRIBUTE` adı *öznitelik Adı* ve değer *özniteliğiDeğer*ile bir öznitelik tanımlar.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a>Test modülü öznitelikleri

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Test modülü `TEST_MODULE_ATTRIBUTE` *testModuleName'ye*bir veya daha fazla makro ile tanımlanan öznitelikleri ekler.

Makro `TEST_MODULE_ATTRIBUTE` adı *öznitelik Adı* ve değer *özniteliğiDeğer*ile bir öznitelik tanımlar.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a>Önceden tanımlanmış öznitelikler

Bu önceden tanımlanmış öznitelik makroları, sık karşılaşılan durumlar için kolaylık sağlamak amacıyla sağlanır. Bunlar, yukarıda açıklanan makronun `TEST_METHOD_ATTRIBUTE` yerine geçilebilir.

```cpp
TEST_OWNER(ownerAlias)
```

A adı `TEST_METHOD_ATTRIBUTE` `Owner` ve *sahibiAlias*öznitelik değeri ile tanımlar.

```cpp
TEST_DESCRIPTION(description)
```

A `TEST_METHOD_ATTRIBUTE` adında `Description` ve *açıklamaöz*değeri ile tanımlar.

```cpp
TEST_PRIORITY(priority)
```

A adında `TEST_METHOD_ATTRIBUTE` `Priority` ve *öznitelik*değeri olan bir önceliği tanımlar.

```cpp
TEST_WORKITEM(workitem)
```

`TEST_METHOD_ATTRIBUTE` *WorkItem'in*adı `WorkItem` ve öznitelik değeri ile bir tanımlar.

```cpp
TEST_IGNORE()
```

A `TEST_METHOD_ATTRIBUTE` adında `Ignore` ve öznitelik değeri ile `true`tanımlar.

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a>CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a>Genel İddialar

#### <a name="are-equal"></a><a name="general_are_equal"></a>Eşittir
İki nesnenin eşit olduğunu doğrulayın

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki çiftin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki şamandıranın eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki char* dizelerinin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki w_char* dizelerinin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a>Eşit Değildir
İki çiftin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki şamandıranın eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki char* dizelerinin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki w_char* dizelerinin eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

İki başvurunun işleç dayalı olarak eşit olmadığını doğrulayın==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a>Aynı
İki başvurunun aynı nesne örneğine (kimlik) atıfta bulunduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a>Aynı değildir
İki başvurunun aynı nesne örneğine (kimlik) başvurmadığını doğrulayın.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a>Null mu
İşaretçinin NULL olduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a>Null değil mi
İşaretçinin NULL olmadığını doğrulama

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a>Doğru mu
Bir koşulun doğru olduğunu doğrulama

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a>Yanlış mı
Bir koşulun yanlış olduğunu doğrulayın

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a>Başarısız
Test çalışması sonucunun başarısız olmasını zorlar

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a>Windows Runtime Asserts

#### <a name="are-equal"></a><a name="winrt_are_equal"></a>Eşittir
İki Windows Runtime işaretçisi eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki Platform::String^ dizelerinin eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a>Aynı
İki Windows Runtime başvurusuaynı nesneye başvurur doğrular.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a>Eşit Değildir
İki Windows Runtime işaretçisi eşit olmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

İki Platform::String^ dizelerinin eşit olmadığını doğrular.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a>Aynı değildir
İki Windows Runtime başvurusuaynı nesneye başvurulmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a>Null mu
Windows Runtime işaretçisi bir nullptr olduğunu doğrular.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a>Null değil mi
Windows Runtime işaretçisi nullptr olmadığını doğrular.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a>Özel Durum İddiaları

#### <a name="expect-exception"></a><a name="expect_exception"></a>Özel Durum Beklentisi
Bir işlevin bir özel durum doğurduğunu doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Bir işlevin bir özel durum doğurduğunu doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a>CppUnitTestLogger.h

### <a name="logger"></a><a name="logger"></a>Günlükçü
Logger **sınıfı, Çıkış Penceresine**yazmak için statik yöntemler içerir.

### <a name="write-message"></a><a name="write_message"></a>Mesaj Yaz
**Çıkış Penceresine** dize yazma

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a>Örnek
Bu kod VSCppUnit kullanımına bir örnektir. Bu öznitelik meta veri, fikstür, iddiaları ile birim testleri ve özel günlük örnekleri içerir.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
