IsAboutToBeFinalized (online hackmd : https://hackmd.io/s/Sk7ylxt3N)
* Used only in Sweeping
  * static void SweepWeakMaps(GCParallelTask* task)
  * void GCRuntime::startSweepingAtomsTable() 
  * IncrementalProgress GCRuntime::sweepAtomsTable(FreeOp* fop,
                                                   SliceBudget& budget)

* Used only in Compacting
  * void Compartment::fixupAfterMovingGC()

* Used in Sweeping and Compacting
  * void Zone::sweepBreakpoints(FreeOp* fop)
  * void Zone::sweepWeakMaps()
  * void Realm::sweepJitRealm()
  * void JitZone::sweep()  // this will call GCHashTable::needsSweep
  * void Debugger::sweepAll(FreeOp* fop)
  * void Realm::sweepDebugEnvironments()
  * void Realm::sweepObjectGroups
  * void Realm::sweepGlobalObject()
  * void Realm::sweepSelfHostingScriptSource()
  * void Realm::sweepTemplateObjects()
  * void Realm::sweepRegExps
  * void Realm::sweepSavedStacks()
  * void JitRuntime::SweepJitcodeGlobalTable(JSRuntime* rt)
  * void Realm::sweepObjectRealm()

* Used in Tenuring
  * void Realm::sweepAfterMinorGC()

* Used in needSweep
  * See AutoSweepObjectGroup/AutoSweepTypeScript
    * js::ObjectGroupRealm::NewEntry::needsSweep
    * js::ObjectGroupRealm::ArrayObjectKey::needsSweep
    * js::ObjectGroupRealm::PlainObjectKey::needsSweep
    * js::ObjectGroupRealm::PlainObjectEntry::needsSweep
    * js::ObjectGroupRealm::AllocationSiteKey::needsSweep
    * js::ObjectGroupRealm::AllocationSiteKey::needsSweep
  * bool JS::Realm::globalIsAboutToBeFinalized()
  * js::InitialShapeEntry::needsSweep

* Not sure/Others (Used in assert, or used outside SM to check object is still alive, or too many callers)
  * void Instance::tracePrivate(JSTracer* trc) // https://searchfox.org/mozilla-central/source/js/src/wasm/WasmInstance.cpp#1386
  * void jit::ToggleBaselineTraceLoggerScripts(JSRuntime* runtime, bool enable) 
  * void jit::ToggleBaselineTraceLoggerEngine(JSRuntime* runtime, bool enable)
  * void JS_UpdateWeakPointerAfterGC(JS::Heap<JSObject*>* objp) 
  * void JS_UpdateWeakPointerAfterGCUnbarriered(JSObject** objp) {
  * JSAtom* AtomsTable::atomizeAndCopyChars(
     JSContext* cx, Chars chars, size_t length, PinningBehavior pin,
     const Maybe<uint32_t>& indexValue, const AtomHasher::Lookup& lookup) 
  * void js::ContextChecks::check
  * void JSScript::finailize(FreeOp* fp)  https://searchfox.org/mozilla-central/rev/cc280c4be94ff8cf64a27cc9b3d6831ffa49fa45/js/src/vm/JSScript.cpp#4092
  * JS::Result<ProxyObject*, JS::OOM&> ProxyObject::create(
     JSContext* cx, const Class* clasp, Handle<TaggedProto> proto,
     gc::AllocKind allocKind, NewObjectKind newKind)
  * bool JS::Realm::hasLiveGlobal() const
  *  Shape* PropertyTreeReadBarrier(Shape* parent, Shape* shape)

* TODO

