                instantsearch/examples/js/e-commerce/polyfills.js at master · algolia/instantsearch · GitHub                                         

[Skip to content](#start-of-content)

Navigation Menu
---------------

Toggle navigation

[](/)

[Sign in](/login?return_to=https%3A%2F%2Fgithub.com%2Falgolia%2Finstantsearch%2Fblob%2Fmaster%2Fexamples%2Fjs%2Fe-commerce%2Fpolyfills.js)

Search or jump to...

Search code, repositories, users, issues, pull requests...
==========================================================

Search

Clear

[Search syntax tips](https://docs.github.com/search-github/github-code-search/understanding-github-code-search-syntax)

Provide feedback
================

We read every piece of feedback, and take your input very seriously.

 Include my email address so I can be contacted

Cancel Submit feedback

Saved searches
==============

Use saved searches to filter your results more quickly
------------------------------------------------------

Name  

Query 

To see all available qualifiers, see our [documentation](https://docs.github.com/search-github/github-code-search/understanding-github-code-search-syntax).

Cancel Create saved search

[Sign in](/login?return_to=https%3A%2F%2Fgithub.com%2Falgolia%2Finstantsearch%2Fblob%2Fmaster%2Fexamples%2Fjs%2Fe-commerce%2Fpolyfills.js)

[Sign up](/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F%3Cuser-name%3E%2F%3Crepo-name%3E%2Fblob%2Fshow&source=header-repo&source_repo=algolia%2Finstantsearch)

You signed in with another tab or window. Reload to refresh your session. You signed out in another tab or window. Reload to refresh your session. You switched accounts on another tab or window. Reload to refresh your session. Dismiss alert

[algolia](/algolia) / **[instantsearch](/algolia/instantsearch)** Public

*   [Notifications](/login?return_to=%2Falgolia%2Finstantsearch) You must be signed in to change notification settings
*   [Fork 504](/login?return_to=%2Falgolia%2Finstantsearch)
*   [Star 3.6k](/login?return_to=%2Falgolia%2Finstantsearch)
    

  Files
-----

 master

/

polyfills.js
============

Blame

Blame

Latest commit
-------------

History
-------

[History](/algolia/instantsearch/commits/master/examples/js/e-commerce/polyfills.js)

[](/algolia/instantsearch/commits/master/examples/js/e-commerce/polyfills.js)

5529 lines (4994 loc) · 198 KB

 master

/

polyfills.js
============

Top

File metadata and controls
--------------------------

*   Code
    
*   Blame
    

5529 lines (4994 loc) · 198 KB

[Raw](https://github.com/algolia/instantsearch/raw/master/examples/js/e-commerce/polyfills.js)

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

67

68

69

70

71

72

73

74

75

76

77

78

79

80

81

82

83

84

85

86

87

88

89

90

91

92

93

94

95

96

97

98

99

100

101

102

103

104

105

106

107

108

109

110

111

112

113

114

115

116

117

118

119

120

121

122

123

124

125

126

127

128

129

130

131

132

133

134

135

136

137

138

139

140

141

142

143

144

145

146

147

148

149

150

151

152

153

154

155

156

157

158

159

160

161

162

163

164

165

166

167

168

169

170

171

172

173

174

175

176

177

178

179

180

181

182

183

184

185

186

187

188

189

190

191

192

193

194

195

196

197

198

199

200

201

202

203

204

205

206

207

208

209

210

211

212

213

214

215

216

217

218

219

220

221

222

223

224

225

226

227

228

229

230

231

232

233

234

235

236

237

238

239

240

241

242

243

244

245

246

247

248

249

250

251

252

253

254

255

256

257

258

259

260

261

262

263

264

265

266

267

268

269

270

271

272

273

274

275

276

277

278

279

280

281

282

283

284

285

286

287

288

289

290

291

292

293

294

295

296

297

298

299

300

301

302

303

304

305

306

307

308

309

310

311

312

313

314

315

316

317

318

319

320

321

322

323

324

325

326

327

328

329

330

331

332

333

334

335

336

337

338

339

340

341

342

343

344

345

346

347

348

349

350

351

352

353

354

355

356

357

358

359

360

361

362

363

364

365

366

367

368

369

370

371

372

373

374

375

376

377

378

379

380

381

382

383

384

385

386

387

388

389

390

391

392

393

394

395

396

397

398

399

400

401

402

403

404

405

406

407

408

409

410

411

412

413

414

415

416

417

418

419

420

421

422

423

424

425

426

427

428

429

430

431

432

433

434

435

436

437

438

439

440

441

442

443

444

445

446

447

448

449

450

451

452

453

454

455

456

457

458

459

460

461

462

463

464

465

466

467

468

469

470

471

472

473

474

475

476

477

478

479

480

481

482

483

484

485

486

487

488

489

490

491

492

493

494

495

496

497

498

499

500

501

502

503

504

505

506

507

508

509

510

511

512

513

514

515

516

517

518

519

520

521

522

523

524

525

526

527

528

529

530

531

532

533

534

535

536

537

538

539

540

541

542

543

544

545

546

547

548

549

550

551

552

553

554

555

556

557

558

559

560

561

562

563

564

565

566

567

568

569

570

571

572

573

574

575

576

577

578

579

580

581

582

583

584

585

586

587

588

589

590

591

592

593

594

595

596

597

598

599

600

601

602

603

604

605

606

607

608

609

610

611

612

613

614

615

616

617

618

619

620

621

622

623

624

625

626

627

628

629

630

631

632

633

634

635

636

637

638

639

640

641

642

643

644

645

646

647

648

649

650

651

652

653

654

655

656

657

658

659

660

661

662

663

664

665

666

667

668

669

670

671

672

673

674

675

676

677

678

679

680

681

682

683

684

685

686

687

688

689

690

691

692

693

694

695

696

697

698

699

700

701

702

703

704

705

706

707

708

709

710

711

712

713

714

715

716

717

718

719

720

721

722

723

724

725

726

727

728

729

730

731

732

733

734

735

736

737

738

739

740

741

742

743

744

745

746

747

748

749

750

751

752

753

754

755

756

757

758

759

760

761

762

763

764

765

766

767

768

769

770

771

772

773

774

775

776

777

778

779

780

781

782

783

784

785

786

787

788

789

790

791

792

793

794

795

796

797

798

799

800

801

802

803

804

805

806

807

808

809

810

811

812

813

814

815

816

817

818

819

820

821

822

823

824

825

826

827

828

829

830

831

832

833

834

835

836

837

838

839

840

841

842

843

844

845

846

847

848

849

850

851

852

853

854

855

856

857

858

859

860

861

862

863

864

865

866

867

868

869

870

871

872

873

874

875

876

877

878

879

880

881

882

883

884

885

886

887

888

889

890

891

892

893

894

895

896

897

898

899

900

901

902

903

904

905

906

907

908

909

910

911

912

913

914

915

916

917

918

919

920

921

922

923

924

925

926

927

928

929

930

931

932

933

934

935

936

937

938

939

940

941

942

943

944

945

946

947

948

949

950

951

952

953

954

955

956

957

958

959

960

961

962

963

964

965

966

967

968

969

970

971

972

973

974

975

976

977

978

979

980

981

982

983

984

985

986

987

988

989

990

991

992

993

994

995

996

997

998

999

1000

/\*

\* Polyfill service v3.111.0

\* For detailed credits and licence information see https://polyfill.io.

\*

\* Features requested: Array.prototype.find,Array.prototype.findIndex,Array.prototype.includes,Object.assign,Object.entries,Promise,default

\*

\* - DocumentFragment, License: CC0

\* - Element.prototype.matches, License: CC0

\* - Element.prototype.closest, License: CC0

\* - Node.prototype.contains, License: CC0

\* - \_DOMTokenList, License: ISC

\* - DOMTokenList, License: CC0

\* - Element.prototype.classList, License: ISC

\* - \_ESAbstract.ArrayCreate, License: CC0

\* - \_ESAbstract.Call, License: CC0

\* - \_ESAbstract.CreateDataProperty, License: CC0

\* - \_ESAbstract.CreateDataPropertyOrThrow, License: CC0

\* - \_ESAbstract.CreateMethodProperty, License: CC0

\* - Object.keys, License: MIT

\* - \_ESAbstract.Get, License: CC0

\* - \_ESAbstract.HasOwnProperty, License: CC0

\* - \_ESAbstract.IsCallable, License: CC0

\* - \_ESAbstract.RequireObjectCoercible, License: CC0

\* - \_ESAbstract.SameValueNonNumber, License: CC0

\* - \_ESAbstract.ToBoolean, License: CC0

\* - \_ESAbstract.ToObject, License: CC0

\* - \_ESAbstract.GetV, License: CC0

\* - \_ESAbstract.GetMethod, License: CC0

\* - \_ESAbstract.Type, License: CC0

\* - Number.isNaN, License: MIT

\* - Object.isExtensible, License: CC0

\* - \_ESAbstract.CreateIterResultObject, License: CC0

\* - \_ESAbstract.GetPrototypeFromConstructor, License: CC0

\* - \_ESAbstract.OrdinaryCreateFromConstructor, License: CC0

\* - \_ESAbstract.IsConstructor, License: CC0

\* - \_ESAbstract.Construct, License: CC0

\* - \_ESAbstract.IsRegExp, License: CC0

\* - \_ESAbstract.IteratorClose, License: CC0

\* - \_ESAbstract.IteratorComplete, License: CC0

\* - \_ESAbstract.IteratorNext, License: CC0

\* - \_ESAbstract.IteratorStep, License: CC0

\* - \_ESAbstract.IteratorValue, License: CC0

\* - \_ESAbstract.OrdinaryToPrimitive, License: CC0

\* - \_ESAbstract.SameValueZero, License: CC0

\* - \_ESAbstract.ToInteger, License: CC0

\* - \_ESAbstract.ToLength, License: CC0

\* - \_ESAbstract.ToPrimitive, License: CC0

\* - \_ESAbstract.ToString, License: CC0

\* - Array.of, License: CC0

\* - Array.prototype.fill, License: CC0

\* - Array.prototype.find, License: CC0

\* - Array.prototype.findIndex, License: CC0

\* - Array.prototype.includes, License: MIT

\* - Event, License: CC0

\* - CustomEvent, License: CC0

\* - Object.getOwnPropertyNames, License: CC0

\* - String.prototype.endsWith, License: CC0

\* - String.prototype.includes, License: CC0

\* - String.prototype.startsWith, License: CC0

\* - \_ESAbstract.ToPropertyKey, License: CC0

\* - Object.getOwnPropertyDescriptor, License: CC0

\* - Object.assign, License: CC0

\* - Symbol, License: MIT

\* - Symbol.iterator, License: MIT

\* - \_ESAbstract.GetIterator, License: CC0

\* - Symbol.species, License: MIT

\* - Map, License: CC0

\* - Set, License: CC0

\* - Array.from, License: CC0

\* - URL, License: CC0-1.0

\* - Symbol.toStringTag, License: MIT

\* - Promise, License: MIT

\* - \_ESAbstract.EnumerableOwnProperties, License: CC0

\* - Object.entries, License: CC0

\* - \_ESAbstract.TrimString, License: CC0

\* - String.prototype.trim, License: CC0

\* - \_mutation, License: CC0

\* - DocumentFragment.prototype.append, License: CC0

\* - DocumentFragment.prototype.prepend, License: CC0

\* - Element.prototype.after, License: CC0

\* - Element.prototype.append, License: CC0

\* - Element.prototype.before, License: CC0

\* - Element.prototype.prepend, License: CC0

\* - Element.prototype.remove, License: CC0

\* - Element.prototype.replaceWith, License: CC0

\*/

(function(self, undefined) {

if (typeof Object.entries !== 'undefined') {

return;

}

// DocumentFragment

(function (global) {

global.DocumentFragment \= function DocumentFragment() {

return document.createDocumentFragment();

};

var fragment \= document.createDocumentFragment();

global.DocumentFragment.prototype \= Object.create(fragment.constructor.prototype)

}(self));

// Element.prototype.matches

Element.prototype.matches \= Element.prototype.webkitMatchesSelector || Element.prototype.oMatchesSelector || Element.prototype.msMatchesSelector || Element.prototype.mozMatchesSelector || function matches(selector) {

var element \= this;

var elements \= (element.document || element.ownerDocument).querySelectorAll(selector);

var index \= 0;

while (elements\[index\] && elements\[index\] !== element) {

++index;

}

return !!elements\[index\];

};

// Element.prototype.closest

Element.prototype.closest \= function closest(selector) {

var node \= this;

while (node) {

if (node.matches(selector)) return node;

else node \= 'SVGElement' in window && node instanceof SVGElement ? node.parentNode : node.parentElement;

}

return null;

};

// Node.prototype.contains

(function() {

function contains(node) {

if (!(0 in arguments)) {

throw new TypeError('1 argument is required');

}

do {

if (this \=== node) {

return true;

}

// eslint-disable-next-line no-cond-assign

} while (node \= node && node.parentNode);

return false;

}

// IE

if ('HTMLElement' in self && 'contains' in HTMLElement.prototype) {

try {

delete HTMLElement.prototype.contains;

// eslint-disable-next-line no-empty

} catch (e) {}

}

if ('Node' in self) {

Node.prototype.contains \= contains;

} else {

document.contains \= Element.prototype.contains \= contains;

}

}());

// \_DOMTokenList

/\*

Copyright (c) 2016, John Gardner

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

\*/

var \_DOMTokenList \= (function() { // eslint-disable-line no-unused-vars

var dpSupport \= true;

var defineGetter \= function (object, name, fn, configurable) {

if (Object.defineProperty)

Object.defineProperty(object, name, {

configurable: false \=== dpSupport ? true : !!configurable,

get: fn

});

else object.\_\_defineGetter\_\_(name, fn);

};

/\*\* Ensure the browser allows Object.defineProperty to be used on native JavaScript objects. \*/

try {

defineGetter({}, "support");

}

catch (e) {

dpSupport \= false;

}

var \_DOMTokenList \= function (el, prop) {

var that \= this;

var tokens \= \[\];

var tokenMap \= {};

var length \= 0;

var maxLength \= 0;

var addIndexGetter \= function (i) {

defineGetter(that, i, function () {

preop();

return tokens\[i\];

}, false);

};

var reindex \= function () {

/\*\* Define getter functions for array-like access to the tokenList's contents. \*/

if (length \>= maxLength)

for (; maxLength < length; ++maxLength) {

addIndexGetter(maxLength);

}

};

/\*\* Helper function called at the start of each class method. Internal use only. \*/

var preop \= function () {

var error;

var i;

var args \= arguments;

var rSpace \= /\\s+/;

/\*\* Validate the token/s passed to an instance method, if any. \*/

if (args.length)

for (i \= 0; i < args.length; ++i)

if (rSpace.test(args\[i\])) {

error \= new SyntaxError('String "' + args\[i\] + '" ' + "contains" + ' an invalid character');

error.code \= 5;

error.name \= "InvalidCharacterError";

throw error;

}

/\*\* Split the new value apart by whitespace\*/

if (typeof el\[prop\] \=== "object") {

tokens \= ("" + el\[prop\].baseVal).replace(/^\\s+|\\s+$/g, "").split(rSpace);

} else {

tokens \= ("" + el\[prop\]).replace(/^\\s+|\\s+$/g, "").split(rSpace);

}

/\*\* Avoid treating blank strings as single-item token lists \*/

if ("" \=== tokens\[0\]) tokens \= \[\];

/\*\* Repopulate the internal token lists \*/

tokenMap \= {};

for (i \= 0; i < tokens.length; ++i)

tokenMap\[tokens\[i\]\] \= true;

length \= tokens.length;

reindex();

};

/\*\* Populate our internal token list if the targeted attribute of the subject element isn't empty. \*/

preop();

/\*\* Return the number of tokens in the underlying string. Read-only. \*/

defineGetter(that, "length", function () {

preop();

return length;

});

/\*\* Override the default toString/toLocaleString methods to return a space-delimited list of tokens when typecast. \*/

that.toLocaleString \=

that.toString \= function () {

preop();

return tokens.join(" ");

};

that.item \= function (idx) {

preop();

return tokens\[idx\];

};

that.contains \= function (token) {

preop();

return !!tokenMap\[token\];

};

that.add \= function () {

preop.apply(that, args \= arguments);

for (var args, token, i \= 0, l \= args.length; i < l; ++i) {

token \= args\[i\];

if (!tokenMap\[token\]) {

tokens.push(token);

tokenMap\[token\] \= true;

}

}

/\*\* Update the targeted attribute of the attached element if the token list's changed. \*/

if (length !== tokens.length) {

length \= tokens.length \>>> 0;

if (typeof el\[prop\] \=== "object") {

el\[prop\].baseVal \= tokens.join(" ");

} else {

el\[prop\] \= tokens.join(" ");

}

reindex();

}

};

that.remove \= function () {

preop.apply(that, args \= arguments);

/\*\* Build a hash of token names to compare against when recollecting our token list. \*/

for (var args, ignore \= {}, i \= 0, t \= \[\]; i < args.length; ++i) {

ignore\[args\[i\]\] \= true;

delete tokenMap\[args\[i\]\];

}

/\*\* Run through our tokens list and reassign only those that aren't defined in the hash declared above. \*/

for (i \= 0; i < tokens.length; ++i)

if (!ignore\[tokens\[i\]\]) t.push(tokens\[i\]);

tokens \= t;

length \= t.length \>>> 0;

/\*\* Update the targeted attribute of the attached element. \*/

if (typeof el\[prop\] \=== "object") {

el\[prop\].baseVal \= tokens.join(" ");

} else {

el\[prop\] \= tokens.join(" ");

}

reindex();

};

that.toggle \= function (token, force) {

preop.apply(that, \[token\]);

/\*\* Token state's being forced. \*/

if (undefined !== force) {

if (force) {

that.add(token);

return true;

} else {

that.remove(token);

return false;

}

}

/\*\* Token already exists in tokenList. Remove it, and return FALSE. \*/

if (tokenMap\[token\]) {

that.remove(token);

return false;

}

/\*\* Otherwise, add the token and return TRUE. \*/

that.add(token);

return true;

};

that.forEach \= Array.prototype.forEach;

return that;

};

return \_DOMTokenList;

}());

// DOMTokenList

/\* global \_DOMTokenList \*/

(function (global) {

var nativeImpl \= "DOMTokenList" in global && global.DOMTokenList;

if (

!nativeImpl ||

(

!!document.createElementNS &&

!!document.createElementNS('http://www.w3.org/2000/svg', 'svg') &&

!(document.createElementNS("http://www.w3.org/2000/svg", "svg").classList instanceof DOMTokenList)

)

) {

global.DOMTokenList \= \_DOMTokenList;

}

// Add second argument to native DOMTokenList.toggle() if necessary

(function () {

var e \= document.createElement('span');

if (!('classList' in e)) return;

e.classList.toggle('x', false);

if (!e.classList.contains('x')) return;

e.classList.constructor.prototype.toggle \= function toggle(token /\*, force\*/) {

var force \= arguments\[1\];

if (force \=== undefined) {

var add \= !this.contains(token);

this\[add ? 'add' : 'remove'\](token);

return add;

}

force \= !!force;

this\[force ? 'add' : 'remove'\](token);

return force;

};

}());

// Add multiple arguments to native DOMTokenList.add() if necessary

(function () {

var e \= document.createElement('span');

if (!('classList' in e)) return;

e.classList.add('a', 'b');

if (e.classList.contains('b')) return;

var native \= e.classList.constructor.prototype.add;

e.classList.constructor.prototype.add \= function () {

var args \= arguments;

var l \= arguments.length;

for (var i \= 0; i < l; i++) {

native.call(this, args\[i\]);

}

};

}());

// Add multiple arguments to native DOMTokenList.remove() if necessary

(function () {

var e \= document.createElement('span');

if (!('classList' in e)) return;

e.classList.add('a');

e.classList.add('b');

e.classList.remove('a', 'b');

if (!e.classList.contains('b')) return;

var native \= e.classList.constructor.prototype.remove;

e.classList.constructor.prototype.remove \= function () {

var args \= arguments;

var l \= arguments.length;

for (var i \= 0; i < l; i++) {

native.call(this, args\[i\]);

}

};

}());

}(self));

// Element.prototype.classList

/\* global \_DOMTokenList \*/

/\*

Copyright (c) 2016, John Gardner

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

\*/

(function (global) {

var dpSupport \= true;

var defineGetter \= function (object, name, fn, configurable) {

if (Object.defineProperty)

Object.defineProperty(object, name, {

configurable: false \=== dpSupport ? true : !!configurable,

get: fn

});

else object.\_\_defineGetter\_\_(name, fn);

};

/\*\* Ensure the browser allows Object.defineProperty to be used on native JavaScript objects. \*/

try {

defineGetter({}, "support");

}

catch (e) {

dpSupport \= false;

}

/\*\* Polyfills a property with a DOMTokenList \*/

var addProp \= function (o, name, attr) {

defineGetter(o.prototype, name, function () {

var tokenList;

var THIS \= this,

/\*\* Prevent this from firing twice for some reason. What the hell, IE. \*/

gibberishProperty \= "\_\_defineGetter\_\_" + "DEFINE\_PROPERTY" + name;

if(THIS\[gibberishProperty\]) return tokenList;

THIS\[gibberishProperty\] \= true;

/\*\*

\* IE8 can't define properties on native JavaScript objects, so we'll use a dumb hack instead.

\*

\* What this is doing is creating a dummy element ("reflection") inside a detached phantom node ("mirror")

\* that serves as the target of Object.defineProperty instead. While we could simply use the subject HTML

\* element instead, this would conflict with element types which use indexed properties (such as forms and

\* select lists).

\*/

if (false \=== dpSupport) {

var visage;

var mirror \= addProp.mirror || document.createElement("div");

var reflections \= mirror.childNodes;

var l \= reflections.length;

for (var i \= 0; i < l; ++i)

if (reflections\[i\].\_R \=== THIS) {

visage \= reflections\[i\];

break;

}

/\*\* Couldn't find an element's reflection inside the mirror. Materialise one. \*/

visage || (visage \= mirror.appendChild(document.createElement("div")));

tokenList \= DOMTokenList.call(visage, THIS, attr);

} else tokenList \= new \_DOMTokenList(THIS, attr);

defineGetter(THIS, name, function () {

return tokenList;

});

delete THIS\[gibberishProperty\];

return tokenList;

}, true);

};

addProp(global.Element, "classList", "className");

addProp(global.HTMLElement, "classList", "className");

addProp(global.HTMLLinkElement, "relList", "rel");

addProp(global.HTMLAnchorElement, "relList", "rel");

addProp(global.HTMLAreaElement, "relList", "rel");

}(self));

// \_ESAbstract.ArrayCreate

// 9.4.2.2. ArrayCreate ( length \[ , proto \] )

function ArrayCreate(length /\* \[, proto\] \*/) { // eslint-disable-line no-unused-vars

// 1. Assert: length is an integer Number e 0.

// 2. If length is -0, set length to +0.

if (1 / length \=== \-Infinity) {

length \= 0;

}

// 3. If length>2^32-1, throw a RangeError exception.

if (length \> (Math.pow(2, 32) \- 1)) {

throw new RangeError('Invalid array length');

}

// 4. If proto is not present, set proto to the intrinsic object %ArrayPrototype%.

// 5. Let A be a newly created Array exotic object.

var A \= \[\];

// 6. Set A's essential internal methods except for \[\[DefineOwnProperty\]\] to the default ordinary object definitions specified in 9.1.

// 7. Set A.\[\[DefineOwnProperty\]\] as specified in 9.4.2.1.

// 8. Set A.\[\[Prototype\]\] to proto.

// 9. Set A.\[\[Extensible\]\] to true.

// 10. Perform ! OrdinaryDefineOwnProperty(A, "length", PropertyDescriptor{\[\[Value\]\]: length, \[\[Writable\]\]: true, \[\[Enumerable\]\]: false, \[\[Configurable\]\]: false}).

A.length \= length;

// 11. Return A.

return A;

}

// \_ESAbstract.Call

/\* global IsCallable \*/

// 7.3.12. Call ( F, V \[ , argumentsList \] )

function Call(F, V /\* \[, argumentsList\] \*/) { // eslint-disable-line no-unused-vars

// 1. If argumentsList is not present, set argumentsList to a new empty List.

var argumentsList \= arguments.length \> 2 ? arguments\[2\] : \[\];

// 2. If IsCallable(F) is false, throw a TypeError exception.

if (IsCallable(F) \=== false) {

throw new TypeError(Object.prototype.toString.call(F) + 'is not a function.');

}

// 3. Return ? F.\[\[Call\]\](V, argumentsList).

return F.apply(V, argumentsList);

}

// \_ESAbstract.CreateDataProperty

// 7.3.4. CreateDataProperty ( O, P, V )

// NOTE

// This abstract operation creates a property whose attributes are set to the same defaults used for properties created by the ECMAScript language assignment operator.

// Normally, the property will not already exist. If it does exist and is not configurable or if O is not extensible, \[\[DefineOwnProperty\]\] will return false.

function CreateDataProperty(O, P, V) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(O) is Object.

// 2. Assert: IsPropertyKey(P) is true.

// 3. Let newDesc be the PropertyDescriptor{ \[\[Value\]\]: V, \[\[Writable\]\]: true, \[\[Enumerable\]\]: true, \[\[Configurable\]\]: true }.

var newDesc \= {

value: V,

writable: true,

enumerable: true,

configurable: true

};

// 4. Return ? O.\[\[DefineOwnProperty\]\](P, newDesc).

try {

Object.defineProperty(O, P, newDesc);

return true;

} catch (e) {

return false;

}

}

// \_ESAbstract.CreateDataPropertyOrThrow

/\* global CreateDataProperty \*/

// 7.3.6. CreateDataPropertyOrThrow ( O, P, V )

function CreateDataPropertyOrThrow(O, P, V) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(O) is Object.

// 2. Assert: IsPropertyKey(P) is true.

// 3. Let success be ? CreateDataProperty(O, P, V).

var success \= CreateDataProperty(O, P, V);

// 4. If success is false, throw a TypeError exception.

if (!success) {

throw new TypeError('Cannot assign value \`' + Object.prototype.toString.call(V) + '\` to property \`' + Object.prototype.toString.call(P) + '\` on object \`' + Object.prototype.toString.call(O) + '\`');

}

// 5. Return success.

return success;

}

// \_ESAbstract.CreateMethodProperty

// 7.3.5. CreateMethodProperty ( O, P, V )

function CreateMethodProperty(O, P, V) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(O) is Object.

// 2. Assert: IsPropertyKey(P) is true.

// 3. Let newDesc be the PropertyDescriptor{\[\[Value\]\]: V, \[\[Writable\]\]: true, \[\[Enumerable\]\]: false, \[\[Configurable\]\]: true}.

var newDesc \= {

value: V,

writable: true,

enumerable: false,

configurable: true

};

// 4. Return ? O.\[\[DefineOwnProperty\]\](P, newDesc).

Object.defineProperty(O, P, newDesc);

}

// Object.keys

/\* global CreateMethodProperty \*/

CreateMethodProperty(Object, "keys", (function() {

'use strict';

// modified from https://github.com/es-shims/object-keys

var has \= Object.prototype.hasOwnProperty;

var toStr \= Object.prototype.toString;

var isEnumerable \= Object.prototype.propertyIsEnumerable;

var hasDontEnumBug \= !isEnumerable.call({ toString: null }, 'toString');

var hasPrototypeEnumBug \= isEnumerable.call(function () { }, 'prototype');

function hasProtoEnumBug() {

// Object.create polyfill creates an enumerable \_\_proto\_\_

var createdObj;

try {

createdObj \= Object.create({});

} catch (e) {

// If this fails the polyfil isn't loaded yet, but will be.

// Can't add it to depedencies because of it would create a circular depedency.

return true;

}

return isEnumerable.call(createdObj, '\_\_proto\_\_')

}

var dontEnums \= \[

'toString',

'toLocaleString',

'valueOf',

'hasOwnProperty',

'isPrototypeOf',

'propertyIsEnumerable',

'constructor'

\];

var equalsConstructorPrototype \= function (o) {

var ctor \= o.constructor;

return ctor && ctor.prototype \=== o;

};

var excludedKeys \= {

$console: true,

$external: true,

$frame: true,

$frameElement: true,

$frames: true,

$innerHeight: true,

$innerWidth: true,

$outerHeight: true,

$outerWidth: true,

$pageXOffset: true,

$pageYOffset: true,

$parent: true,

$scrollLeft: true,

$scrollTop: true,

$scrollX: true,

$scrollY: true,

$self: true,

$webkitIndexedDB: true,

$webkitStorageInfo: true,

$window: true

};

var hasAutomationEqualityBug \= (function () {

if (typeof window \=== 'undefined') { return false; }

for (var k in window) {

try {

if (!excludedKeys\['$' + k\] && has.call(window, k) && window\[k\] !== null && typeof window\[k\] \=== 'object') {

try {

equalsConstructorPrototype(window\[k\]);

} catch (e) {

return true;

}

}

} catch (e) {

return true;

}

}

return false;

}());

var equalsConstructorPrototypeIfNotBuggy \= function (o) {

if (typeof window \=== 'undefined' || !hasAutomationEqualityBug) {

return equalsConstructorPrototype(o);

}

try {

return equalsConstructorPrototype(o);

} catch (e) {

return false;

}

};

function isArgumentsObject(value) {

var str \= toStr.call(value);

var isArgs \= str \=== '\[object Arguments\]';

if (!isArgs) {

isArgs \= str !== '\[object Array\]' &&

value !== null &&

typeof value \=== 'object' &&

typeof value.length \=== 'number' &&

value.length \>= 0 &&

toStr.call(value.callee) \=== '\[object Function\]';

}

return isArgs;

}

return function keys(object) {

var isFunction \= toStr.call(object) \=== '\[object Function\]';

var isArguments \= isArgumentsObject(object);

var isString \= toStr.call(object) \=== '\[object String\]';

var theKeys \= \[\];

if (object \=== undefined || object \=== null) {

throw new TypeError('Cannot convert undefined or null to object');

}

var skipPrototype \= hasPrototypeEnumBug && isFunction;

if (isString && object.length \> 0 && !has.call(object, 0)) {

for (var i \= 0; i < object.length; ++i) {

theKeys.push(String(i));

}

}

if (isArguments && object.length \> 0) {

for (var j \= 0; j < object.length; ++j) {

theKeys.push(String(j));

}

} else {

for (var name in object) {

if (!(hasProtoEnumBug() && name \=== '\_\_proto\_\_') && !(skipPrototype && name \=== 'prototype') && has.call(object, name)) {

theKeys.push(String(name));

}

}

}

if (hasDontEnumBug) {

var skipConstructor \= equalsConstructorPrototypeIfNotBuggy(object);

for (var k \= 0; k < dontEnums.length; ++k) {

if (!(skipConstructor && dontEnums\[k\] \=== 'constructor') && has.call(object, dontEnums\[k\])) {

theKeys.push(dontEnums\[k\]);

}

}

}

return theKeys;

};

}()));

// \_ESAbstract.Get

// 7.3.1. Get ( O, P )

function Get(O, P) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(O) is Object.

// 2. Assert: IsPropertyKey(P) is true.

// 3. Return ? O.\[\[Get\]\](P, O).

return O\[P\];

}

// \_ESAbstract.HasOwnProperty

// 7.3.11 HasOwnProperty (O, P)

function HasOwnProperty(o, p) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(O) is Object.

// 2. Assert: IsPropertyKey(P) is true.

// 3. Let desc be ? O.\[\[GetOwnProperty\]\](P).

// 4. If desc is undefined, return false.

// 5. Return true.

// Polyfill.io - As we expect user agents to support ES3 fully we can skip the above steps and use Object.prototype.hasOwnProperty to do them for us.

return Object.prototype.hasOwnProperty.call(o, p);

}

// \_ESAbstract.IsCallable

// 7.2.3. IsCallable ( argument )

function IsCallable(argument) { // eslint-disable-line no-unused-vars

// 1. If Type(argument) is not Object, return false.

// 2. If argument has a \[\[Call\]\] internal method, return true.

// 3. Return false.

// Polyfill.io - Only function objects have a \[\[Call\]\] internal method. This means we can simplify this function to check that the argument has a type of function.

return typeof argument \=== 'function';

}

// \_ESAbstract.RequireObjectCoercible

// 7.2.1. RequireObjectCoercible ( argument )

// The abstract operation ToObject converts argument to a value of type Object according to Table 12:

// Table 12: ToObject Conversions

/\*

|----------------------------------------------------------------------------------------------------------------------------------------------------|

| Argument Type | Result |

|----------------------------------------------------------------------------------------------------------------------------------------------------|

| Undefined | Throw a TypeError exception. |

| Null | Throw a TypeError exception. |

| Boolean | Return argument. |

| Number | Return argument. |

| String | Return argument. |

| Symbol | Return argument. |

| Object | Return argument. |

|----------------------------------------------------------------------------------------------------------------------------------------------------|

\*/

function RequireObjectCoercible(argument) { // eslint-disable-line no-unused-vars

if (argument \=== null || argument \=== undefined) {

throw TypeError(Object.prototype.toString.call(argument) + ' is not coercible to Object.');

}

return argument;

}

// \_ESAbstract.SameValueNonNumber

// 7.2.12. SameValueNonNumber ( x, y )

function SameValueNonNumber(x, y) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(x) is not Number.

// 2. Assert: Type(x) is the same as Type(y).

// 3. If Type(x) is Undefined, return true.

// 4. If Type(x) is Null, return true.

// 5. If Type(x) is String, then

// a. If x and y are exactly the same sequence of code units (same length and same code units at corresponding indices), return true; otherwise, return false.

// 6. If Type(x) is Boolean, then

// a. If x and y are both true or both false, return true; otherwise, return false.

// 7. If Type(x) is Symbol, then

// a. If x and y are both the same Symbol value, return true; otherwise, return false.

// 8. If x and y are the same Object value, return true. Otherwise, return false.

// Polyfill.io - We can skip all above steps because the === operator does it all for us.

return x \=== y;

}

// \_ESAbstract.ToBoolean

// 7.1.2. ToBoolean ( argument )

// The abstract operation ToBoolean converts argument to a value of type Boolean according to Table 9:

/\*

\--------------------------------------------------------------------------------------------------------------

| Argument Type | Result |

\--------------------------------------------------------------------------------------------------------------

| Undefined | Return false. |

| Null | Return false. |

| Boolean | Return argument. |

| Number | If argument is +0, -0, or NaN, return false; otherwise return true. |

| String | If argument is the empty String (its length is zero), return false; otherwise return true. |

| Symbol | Return true. |

| Object | Return true. |

\--------------------------------------------------------------------------------------------------------------

\*/

function ToBoolean(argument) { // eslint-disable-line no-unused-vars

return Boolean(argument);

}

// \_ESAbstract.ToObject

// 7.1.13 ToObject ( argument )

// The abstract operation ToObject converts argument to a value of type Object according to Table 12:

// Table 12: ToObject Conversions

/\*

|----------------------------------------------------------------------------------------------------------------------------------------------------|

| Argument Type | Result |

|----------------------------------------------------------------------------------------------------------------------------------------------------|

| Undefined | Throw a TypeError exception. |

| Null | Throw a TypeError exception. |

| Boolean | Return a new Boolean object whose \[\[BooleanData\]\] internal slot is set to argument. See 19.3 for a description of Boolean objects. |

| Number | Return a new Number object whose \[\[NumberData\]\] internal slot is set to argument. See 20.1 for a description of Number objects. |

| String | Return a new String object whose \[\[StringData\]\] internal slot is set to argument. See 21.1 for a description of String objects. |

| Symbol | Return a new Symbol object whose \[\[SymbolData\]\] internal slot is set to argument. See 19.4 for a description of Symbol objects. |

| Object | Return argument. |

|----------------------------------------------------------------------------------------------------------------------------------------------------|

\*/

function ToObject(argument) { // eslint-disable-line no-unused-vars

if (argument \=== null || argument \=== undefined) {

throw TypeError();

}

return Object(argument);

}

// \_ESAbstract.GetV

/\* global ToObject \*/

// 7.3.2 GetV (V, P)

function GetV(v, p) { // eslint-disable-line no-unused-vars

// 1. Assert: IsPropertyKey(P) is true.

// 2. Let O be ? ToObject(V).

var o \= ToObject(v);

// 3. Return ? O.\[\[Get\]\](P, V).

return o\[p\];

}

// \_ESAbstract.GetMethod

/\* global GetV, IsCallable \*/

// 7.3.9. GetMethod ( V, P )

function GetMethod(V, P) { // eslint-disable-line no-unused-vars

// 1. Assert: IsPropertyKey(P) is true.

// 2. Let func be ? GetV(V, P).

var func \= GetV(V, P);

// 3. If func is either undefined or null, return undefined.

if (func \=== null || func \=== undefined) {

return undefined;

}

// 4. If IsCallable(func) is false, throw a TypeError exception.

if (IsCallable(func) \=== false) {

throw new TypeError('Method not callable: ' + P);

}

// 5. Return func.

return func;

}

// \_ESAbstract.Type

// "Type(x)" is used as shorthand for "the type of x"...

function Type(x) { // eslint-disable-line no-unused-vars

switch (typeof x) {

case 'undefined':

return 'undefined';

case 'boolean':

return 'boolean';

case 'number':

return 'number';

case 'string':

return 'string';

case 'symbol':

return 'symbol';

default:

// typeof null is 'object'

if (x \=== null) return 'null';

// Polyfill.io - This is here because a Symbol polyfill will have a typeof \`object\`.

if ('Symbol' in self && (x instanceof self.Symbol || x.constructor \=== self.Symbol)) return 'symbol';

return 'object';

}

}

// Number.isNaN

/\* global CreateMethodProperty, Type \*/

(function () {

var that \= self;

// 20.1.2.4. Number.isNaN ( number )

CreateMethodProperty(Number, 'isNaN', function isNaN(number) {

// 1. If Type(number) is not Number, return false.

if (Type(number) !== 'number') {

return false;

}

// 2. If number is NaN, return true.

if (that.isNaN(number)) {

return true;

}

// 3. Otherwise, return false.

return false;

});

}());

// Object.isExtensible

/\* global CreateMethodProperty, Type \*/

(function (nativeIsExtensible) {

// 19.1.2.13 Object.isExtensible ( O )

CreateMethodProperty(Object, 'isExtensible', function isExtensible(O) {

// 1. If Type(O) is not Object, return false.

if (Type(O) !== "object") {

return false;

}

// 2. Return ? IsExtensible(O).

return nativeIsExtensible ? nativeIsExtensible(O) : true;

});

}(Object.isExtensible));

// \_ESAbstract.CreateIterResultObject

/\* global Type, CreateDataProperty \*/

// 7.4.7. CreateIterResultObject ( value, done )

function CreateIterResultObject(value, done) { // eslint-disable-line no-unused-vars

// 1. Assert: Type(done) is Boolean.

if (Type(done) !== 'boolean') {

throw new Error();

}

// 2. Let obj be ObjectCreate(%ObjectPrototype%).

var obj \= {};

// 3. Perform CreateDataProperty(obj, "value", value).

CreateDataProperty(obj, "value", value);

// 4. Perform CreateDataProperty(obj, "done", done).

CreateDataProperty(obj, "done", done);

// 5. Return obj.

return obj;

}

// \_ESAbstract.GetPrototypeFromConstructor

/\* global Get, Type \*/

// 9.1.14. GetPrototypeFromConstructor ( constructor, intrinsicDefaultProto )

function GetPrototypeFromConstructor(constructor, intrinsicDefaultProto) { // eslint-disable-line no-unused-vars

// 1. Assert: intrinsicDefaultProto is a String value that is this specification's name of an intrinsic object. The corresponding object must be an intrinsic that is intended to be used as the \[\[Prototype\]\] value of an object.

// 2. Assert: IsCallable(constructor) is true.

// 3. Let proto be ? Get(constructor, "prototype").

var proto \= Get(constructor, "prototype");

// 4. If Type(proto) is not Object, then

if (Type(proto) !== 'object') {

// a. Let realm be ? GetFunctionRealm(constructor).

// b. Set proto to realm's intrinsic object named intrinsicDefaultProto.

proto \= intrinsicDefaultProto;

}

// 5. Return proto.

return proto;

}

// \_ESAbstract.OrdinaryCreateFromConstructor

/\* global GetPrototypeFromConstructor \*/

// 9.1.13. OrdinaryCreateFromConstructor ( constructor, intrinsicDefaultProto \[ , internalSlotsList \] )

function OrdinaryCreateFromConstructor(constructor, intrinsicDefaultProto) { // eslint-disable-line no-unused-vars

var internalSlotsList \= arguments\[2\] || {};

// 1. Assert: intrinsicDefaultProto is a String value that is this specification's name of an intrinsic object.

// The corresponding object must be an intrinsic that is intended to be used as the\[\[Prototype\]\] value of an object.

[View remainder of file in raw view](https://github.com/algolia/instantsearch/raw/master/examples/js/e-commerce/polyfills.js)

You can’t perform that action at this time.