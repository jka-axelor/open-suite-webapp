## [6.4.5] (2023-02-03)

#### Fixed

* Payment: cancelling a payment from an Invoice or an Expense must go through the reverse of the move:

When registering a payment in an invoice or an expense, the move generated will often be in Daybook mode.
So the cancel button of the payment will indicate to the user that cancelling this Invoice/Expense payment must 
be done by reversing the corresponding move.
If the move generated from the payment is not accounted, it will be deleted, and the Invoice/Expense payment will be cancelled.

* Payment voucher: fixed amount remaining to pay when we duplicate a move.
* Accounting report: fixed partner grouping issue on preparatory process for fees declaration.
* Cheque rejection: fixed an issue where we were unable to select a payment voucher.
* User: fixed active user being able to change its user code.
* Sale order: fixed a bug where doing a partial invoicing in percentage could not work.
* Company bank details: fixed company bank details filter in invoice and purchase order form views.
* Accounting batch: fixed possible inconsistencies by blocking move generation if the status between the operation journal and the selected cut off move are not compatible.
* BPM: Fix view attrs and dmn expression builders

  - Add meta attrs support in view attrs
  - Display all models from all pools in view attrs
  - Fix blank screen when editing a column properties in DMN editor
  - Fix incomplete selection when using models for output in DMN editor

* Stock move: fixed rounding issues when computing the total to avoid a gap between order/invoice totals and related stock moves totals.
* Stock move: fixed report not showing manually changed address for customer delivery.
* Cost calculation: fixed the priority on the bill of materials chosen during the calculation process. This fixes an issue where a bill of materials from another company was used to compute the cost.
* Fiscal position: changed the behavior of fiscal position on purchase and sale order:

Now the partner is filtered depending on the currency and price list which are readonly if there is an order line.
The fiscal position is now editable even if there is an order line. Changing the partner updates the fiscal position and the taxes on lines.

* Accounting report: fixed an issue were move lines with no partner were not displayed in the report.
* Accounting report: corrected wrong values in 2054 accounting report.
* Payment session: fixed payment session cash move line generation by correcting the amount in move lines.
* Bank reconciliation: fixed unselect button disappearing when we customize the grid.
* Payment condition: add a warning message on payment condition modification if the payment condition is used on existing records.
* Product: updated condition for default value on product pulled off market date.
* Manufacturing order: fixed small UI issue in form view.
* Analytic move line query: fixed an issue were analytic axes not linked to a company were not displayed.
* Partner: fixed an issue where multiple error messages were displayed if the partner bank details was invalid.
* Account management: fixed demo data import.
* Sale order/Purchase order/Invoice line: fixed JNPE error occured when fetching the correct translation for code and description.
* Studio: inserting fields is now easier.
* Invoice term: fixed error on creation of new invoice term on a new invoice.
* Sale order printing: correctly hide discount related rows when the sale order is configured to hide discounts.
* Move consolidation: fixed errors during move consolidation happening when analytic distribution line were missing information.
* Subrogation release: fixed an issue where supplier invoices were retrieved with customer invoices.
* Account management: fixed an issue preventing any user from adding an account management of type tax in the financial configuration.
* Fixed asset category: clear company related fields when changing or clearing the company field to avoid inconsistencies.
* Fixed asset: clear company related fields when changing or clearing the company field to avoid inconsistencies.
* Fixed asset: set default value to 0 to avoid saving a wrong default value in the fields Disposal Type and Quantity type on new and ongoing fixed asset.
* Fixed asset: improved UI for the 'Update depreciating settings' feature.
* Fixed asset: fixed filter on partner field in form view.
* Account config: fixed an issue were financial discount related configuration were required.
* Purchase order: duplicating a purchase order now correctly resets budget.
* Bill of materials: fixed an issue where the label 'BOM by default' was displayed on a new bill of materials.

## [6.4.4] (2023-01-19)

#### Fixed

* Inventory: Reversed Gap computation on inventory lines. Previously, the gap value was negative when the quantity found in the inventory was greater than the expected quantity. It is now positive in this case and negative if we have less quantity than expected.
* Stock move: fixed a regression were it was impossible to select any product on internal move.
* Contracts: fixed an issue where, when filling a product in a contract line, "missing configuration" errors were not shown to the user.
* Manufacturing order: fixed a bug where outsourced manufacturing orders could not be planned because 'outsourcing receipt stock location' was missing in the stock config.
* TranslationService: fixed an issue happening when using a translatable field, when the translation key is equal to the value, the wrong translation was displayed.
* Company: add explicit error message if the current user active company is not set and needed.
* Accounting batch: fix annual closing move generation.
* Accounting batch: fixed "PersistenceException" error preventing the execution of the batch when the list of opening account was empty.
* Accounting batch: fixed an issue where Payment reminder report was not generated.
* Accounting batch: fixed status of moves generated by annual closure batch by accounting them during the process.
* Accounting batch Close/open annual accounts: added error gestion for persistence exception.
* Accounting batch: the batch controlling move consistency was only checking daybook moves, fixed this behavior so this batch is now also checking accounted moves.
* Accounting reports: UI improvement for the form view (hide "global" and "global by date" fields for General balance and Partner balance).
* Accounting report: restored both DAS2 reports according to the initial specifications.
* Accounting report: fixed column C of impairment value table of the DGI 2055 accounting report.
* Accounting report: fix accounting report 2055 wrong column A.
* Bank reconciliation: fixed a UI issue where clicking "Unselected" with a selected move line breaks the alignement of the blue buttons in the move line grid.
* Period: fixed an issue preventing to reopen a period that was closed permanently or temporarily.
* Quality measuring point: set a minimum of 1 for the coefficient.
* Fixed asset: fix typos in french translation that appeared in the popup when using "Tools" in grid view.
* Fixed asset: fix wrong disposal depreciation value when disposing just before the last depreciation line, with prorata temporis.
* Accounting: correct demo data to correctly manage reverse vat on intra-eu purchases.
* Bank order: fix payment mode selection and set accounting move trigger select required:

Payment mode with Immediate move generation trigger settings can now be chosen in a bank order.
Accounting trigger move select is now required and not automatically filled when creating a new bank order.

* Complementary products: fixed an issue where the quantity of complementary products were multiplied by the quantity of the main product (when using the configuration "manage multiple sale quantity").
* Move/Analytic distribution: fixed an issue were saving a modification on analytic distribution in move line was not working correctly.
* Move template: fixed issues on move generation from a template causing the generated move to not display some fields and to have duplicated analytic lines on move lines.
* Period: fixed an error preventing a period from being closed.
* Invoice: fixed an issue which removed the product name when changing the quantity in a line.
* Invoice: fixed a bug where the lines of a advance payment could be duplicated from a purchase order with reversed charge tax line.
* Invoice: when generating an interco invoice, the generated supplier invoice now takes the correct company bank details.
* Invoice: fixed error on ventilation when we have an payment condition with a line with hold back option.
* Address: fixed an UI issue where changing the zip code was emptying the city.
* EBICS: restore proxy support for EBICS communications.

## [6.4.3] (2023-01-05)

#### Fixed

* Accounting report: fixed presentation in excel output for AccountingReportType15.
* Fixed asset: fix error message when realizing a derogatory line with a category that lacks one of the derogatory depreciation accounts.
* Sale order, stock move, purchase order: fixed an issue where a NPE error was displayed when adding a new line in sale order, sale order template, stock move, purchase order.
* Accounting report: fixed move lines retrieval on DAS2 Proof, given das2 activity and service type.
* Move line query: fixed filter when partner field is not filled.
* Fixed asset category: Rename some accounts in accounting tab.
* Bank details: improve message when confirming a bank order and a receiver bank details is inactive.
* Invoice term: delete reason of refusal to pay when accepting PFP.
* Payment voucher: fix generated payment move given financial discount tax amount.
* Fixed asset: Fix wrong depreciation value computation in fixed asset line till the depreciation date for both linear and degressive depreciation plan.
* Substitute pfp validator: added a control on dates so start date cannot be after end date.
* Move line: take into consideration isTaxAuthorizedOnMoveLine from account for the auto completion.
* Move: fixed an issue where description was not filled during move origin change.
* Expense: fixed an issue where ground for refusal was hidden even if it was filled.
* Manufacturing: fix form views for subcontractor deliveries and arrivals.
* Move template line: Hide distribution template field if selected account does not have analytic distribution authorized.
* Analytic distribution: add filter for analytic axis, using the account config of the company.
* Invoice: add missing translations on tab titles.
* Followers: Fixed a residual bug where trying to fetch a recipient would result in a exception with somes conditions
* Followers: Fixed a residual bug where trying to fetch a recipient would result in a exception with somes conditions.
* Fixed asset: sale move generation is now correctly based on sale account.
* Move line: fixed an issue where base analytic distribution was readonly while the configuration allowed the modification.
* MRP: fixed an infinite loop issue

An infinite loop occurred when, for a product, the available stock was less than the minimum quantity of its stock rule
and this product was used in a purchase order.

* MRP: fix generation proposal menu for more clarity.

Generate proposal menu item now opens a wizard with 2 buttons:
One for generating all possible proposals, one for generating proposals of only selected lines.

* MRP: fixed NPE error that could happen during MRP computation if a operation order had a null planned start date.
* MRP: When generating purchase order from proposals, correctly fill desired delivery date.
* Fixed Asset: add filter by purchase journal in purchase account move field.
* Fixed asset category: fixed some french translation in accounting information panel.
* Move line/analytic: fixed an issue where analytic was not generated during move line generation.
* Invoice term: fixed the issue making the partner form blank.
* Accounting Report: add filter by company on AccountingReportType22.
* Invoice: reject company bank details when default bank details is not active.
* Fixed asset: fixed disposalValue when disposing by scrapping, hide disposalValue when asset is disposed by cession.
* Fixed asset: fixed issue with prorata temporis when computation date starts on the 31st of months.
* MoveLineQuery: Change design of isSelected field.
* Cost sheet: fixed wrong human cost calculation when computing a cost sheet for a in progress manufacturing order.
* Bank reconciliation: added default account type in search query.
* Analytic distribution: make analytic distribution required on invoice lines given the account configuration, check added on analytic move line to ensure a total of 100% by axis.
* Demo data: complete demo data for permissions, roles and menus.
* Move: currency related fields are now changed on change of company
* Inventory: when changing real quantity in a line, now takes the correct wap price into account when computing gap and real value.
* Contracts: correctly apply the configuration "Nb of digits for unit prices" to price in contract lines.
* Contracts: correctly apply the configuration "Nb of digits for quantity" to price in contract lines.
* Accounting report type: UI form view improvements.
* Move: fix creation of an move line when an partner has a default charge account.
* BPM: Add meta attrs support in view attrs and fix built in variable support.
* Manufacturing Orders: during manfacturing order generation, added a more explicit message if the bill of materials has 0 quantity.
* Accounting report: Fix filter by account on "vat statement received" report.
* Timesheet line: fixed task display in grid view.
* Aged balance report: corrected wrong currency amount displayed and corrected non due amount displayed in wrong column.
* Sale order separation: fixed computation of miscellaneous sale order fields.
* Accounting report: fixed an issue where 0.0 figures were wrongly displayed in title lines for PDF personnalized reports.
* Move/Move line: fixed deletion of analytic axis and remove save popup when nothing is edited on move line.
* Move template: add partner on the generated move when there is only one.
* Bank reconciliation: fixed display of move description in BankReconciliation reports.
* Accounting report: fixed different issues on ETAT PREPARATOIRE DGI 2054.
* Fixed asset: fixed issues with prorata-temporis on depreciation plan computation of imported fixed assets.
* Accounting report: fixed DAS2 proof declaration report to only display reconciled move lines and purchase moves on printing.

## [6.4.2] (2022-12-16)

#### Features

* Year: Demo data for civil, fiscal and payroll years are now based on the current year.

Add the possibility to fix a date element when using TODAY in demo data with equal sign.
Example: TODAY[-4y=1M=1d] will give us 2018-01-01 if we are in 2022.


#### Fixed

* Bill of materials: fix error when accessing general bill of materials menu.
* Invoice: fixed an error occurring when total A.T.I was equal to zero.
* Leave request: fix error message when sending leave request when company is missing.
* Accounting reports: add origin informations (ref and date) on general ledger and partner general ledger.
* Move line: clear fields related to partner when partner is emptied.
* Invoice: correctly hide refund list when there is no refund.
* Invoice: fixed an error occurring when creating a line without product.
* Move: on move generation from template view, correctly set "generate move" button as readonly when there is no input.
* Task editor: fix error while dragging task.
* Partner address: improve UI when adding an address to a partner to avoid inconsistencies.
* Menu builder: eval is automatically added for context value fixed.
* Menu builder: set context by default when overriding an existing menu.
* Account management: set default values when we create a new record in account management grid.
* Purchase Order: add missing translation when generating advance payment.
* Debt recovery history: prevent the user from inserting new rows in grid view.
* Bank Order: Payment mode and file format now are correctly reset when order type select is changed.
* Stock move: picking order comments panel are now correctly hidden for supplier arrivals.
* Purchase order report: fixed an issue where product name was displayed instead of specific supplier product name.
* Fixed asset category: filter IFRS account fields by charge account type.
* Accounting report: fixed wrongly defined display condition on analytic axis, analytic account, account type fields for analytic type reports form view.
* Translation: fix wrong french translation for Ongoing.
* Purchase order: now correctly takes the default virtual supplier stock location when creating a purchase order.
* Bank statement rule: Add filter on counter part account to avoid selecting view accounts.
* Product details: fixed permission so users do not need write permissions on Product to use this feature.
* Stock move: fixed query exception that happened on the form view when the user had no active company.
* Contract / ContractVersion: allow to correctly fill dates when 'isPeriodicInvoicing' is activated on a new contract version.
* Account Management : Add filter by company on journal field.
* Expense: now takes the correct bank details when registering a payment.
* Data Backup: fixed an error occurring when creating a data backup with the anonymization enabled.

## [6.4.1] (2022-12-08)

#### Features

* Invoice: add new French statements in Invoice Report depending of product type.
* Invoice: add partner siret number in French report.

#### Fixed

* Move line query: partner field is no more required in database and views.
* Reconcile: optimization were made to reduce execution time on all accounting processes related to reconciliation.
* User: email field is now correctly displayed

Email field is now displayed in editing mode.
Email field is now displayed in readonly mode only if a value is present.

* Followers: fixed a bug where trying to fetch a recipient would result in a exception with somes conditions.
* Sale order: fixed stack overflow error when the partner had a parent partner.
* Cash management: fixed an issue were some data were not displayed correctly on the PDF report.
* Invoice line: choosing a product from a supplier catalog now takes the product name from the supplier catalog and not the translation.
* Payment session: fix confirming a bank order generated from a payment session when the bank order lines had different dates.
* Invoice tax line: set vat system to default value when tax line value is 0.
* Leave request / employee: a HR manager can now access draft requests for other employees from the menu.
* Fix creation of new invoice term from moves and invoices.
* Accounting move: fix NPE when modifying move lines on a duplicated move.
* Accounting move: when we reverse a move, the analytic move lines are now correctly kept on the reversed move.
* Account config: add missing sequences of analytic axis in demo datas.
* Debt recovery history: prevent the user from printing a report when there is no debt recovery.
* Fixed asset: fixed disposal move not generated when proceeding to the disposal of a fixed asset where accounting value is equal to 0.
* Fixed asset: fixed wrong accounting value in degressive computation.
* Fixed asset: fixed tax lines management in cession sale move generation

Check on missing tax account only when the tax line value is positive
Initialize of taxline in movelines for credit move line and tax move line

* Move line: fix typo in french error message.
* Payment voucher: change payment voucher element lists to display the moveline origin instead of the invoice directly.
* Move Template: rework of tax management
  - Tax move lines are now selectable just for preview.
  - Recompute of tax move lines via other move lines with tax on it.
  - Message when a tax move line is set to inform user.

* Stock move: changing the real quantity of a line will not reset the discounted price to the original price anymore.

When generating a Stock move from a Purchase order, if a line had a discount,
changing the real quantity of a discounted line would set the price to the original one. This wrong behavior is now fixed.

* Journal: "Has required origin" boolean french help text have been corrected.
* Sale order : Fixed the automatic filling when partner change for the field 'Hide discount on prints' according to it value in the price list.
* Price List: fixed wrong filter on price list menu entry.
* Stock move mass invoicing: fixed a bug where some stock moves were not be invoiced when the invoice was created from a merge.
* Accounting batch: Fix the batch to realize fixed asset line so it correctly update only the fixed asset lines from the selected company.
* Operation order: fix a blocking NullPointerException error when we plan an operation order without a machine.
* Sequence / Forecast recap: Fix demo data sequence for the forecast recap.
* Accounting dashboard: fix not opening the right grid when clicking on the rejection reason pie chart.
* Invoice: when trying to ventilate an invoice, fixed a case where rounding issue happened preventing the ventilation.
* Accounting report : fix DAS2 printing
* Stock move: details stock locations lines will not longer be generated with zero quantity when the stock move is a delivery. This change will allow to correctly use auto generation of tracking number for sales.
* Bank order: Add the possibility to sign bank orders even without EBICS module.
* Sale/Purchase order: fix the way we fetch default stock location on purchase and sale orders using partner stock settings.
* Expense: when paying expense, correctly fill sender company and sender bank details in the generated payment.
* Accounting demo data: fix demo data for fixed asset category and journals.
* Discounted payment move: corrected discounted payment move been not balanced.
* Invoice payment: corrected discount fields not displayed in invoice payment.
* Payment voucher: fix amount controls on payment given auto imputation and financial discount.
* Accounting move line: fix currency amount/rate readonly condition in the counterpart generation.
* Stock move: if the configuration is active, services (product) are now correctly managed in stock moves.

## [6.4.0] (2022-11-28)

#### Features

* Invoice Terms:

Add a new feature to manage multiple terms for invoicing.
A new “invoice terms” table has been added on invoices and on associated move lines.
By configuring payment conditions and selecting them on an invoice these terms are automatically generated.
This new feature is now used every time we pay any invoice from any process (move lettering, payment session, payment voucher, …).

* Cut off:

  * Manage cut off process on invoices and moves.
  * Add a preview option in the cut off batch.
  * Add new configurations to select cut off accounts.
  * The configurations and the batch are now moved from supplychain to accounting module.

* Payment Session:

Introduce a new UI to allow financial department employees to generate outgoing payments in mass or generate direct debit for incoming payments.
The feature include, depending on whether the options have been activated, a search and selection screen for all invoice terms to be paid depending on search criterias (payment mode, due date, financial discount) and the generation of related accounting moves and the associated bank orders (SEPA or International wire transfer or direct debit).
The payment session only works at the moment in the company currency.

* VAT:

The way VAT is working has been reviewed to better fit with usages. The configuration determining the type of VAT (on Deliveries/Invoicing Vs Payments) has been removed from the tax allowing the use of a single tax record for companies selling goods and services. The new feature includes a set of two fields (on partner and accounts) to determine the regime/system that applies. VAT reports are updated with the new system.

* Deposit slip: cheque deposit slip report complete rework.
* Analytic Account: manage analytic account by company

Allow an analytic account to be linked to a company so the analytic account can be shared between all companies or can be assigned to a specific company.

* Annual Closure : Improve annual closure and new closure assistant.

Now specific journals can be open or closed on the period. This feature is also taken into account in the annual closure accounting batch.
In the annual closure accounting batch possibility to generate the result move if the year accounts are opened.
New accounting batch “Control moves consistency” (“Contrôle des écritures”) to check daybook moves before the annual closure in order to check if daybook moves can be automatically accounted.
A new closure assistant allows you to follow the fiscal year closure step by step (possibility to see the step, open the action, validate or cancel it).
At the close of a year, all linked periods are automatically closed.

* Studio : UI improvement and changes

  * Support of icon and color for selection builder.
  * Set required field in red Ergonomy view.
  * Add pattern on name in custom objects.
  * Fix panel bugs.
  * Use color for fields icon.
  * Deletion popup next to the field.
  * Graphical offset when selecting a spacer.

* Mapper : UI improvement and changes

  * Remove search fields column and replace 'Search' value from option 'Query'
  * Add query builder for value column when 'Value from' is 'Query'
  * Add 'Built-Ins Variables' option allow to select built in variables when 'Value from' is 'Context'
  * Add 'Condition' column with expression builder to create condition for selected field
  * Add 'Save' new boolean option for save the new or existing record by generated script
  * Display required fields in red

* BPM : UI improvement and changes

  * Migrate BPM query builder with generic builder
  * Migrate mapper changes with bpm mapper
  * Support item as buttons on user task
  * Support item as buttons in View Attributes of task


#### Changes

* MRP: add new scheduler to run MRP at predefined times.
* Please note following database changes for MRP:
    * Added new fields name and fullName (mrpSeq + name)
    * Added a unicity constraint on mrpSeq

* MRP: Manufacturing order proposals (and their needs) are now set with an appropriate maturity date by taking into account the duration of the manufacturing order.

* Bank reconciliation: Added a new process allowing to correct a reconciliation even after its validation.
* PurchaseOrder : do not manage budget exceed in supplychain module

The budget exceed check called when requesting a purchase order can no longer be managed from supplychain module, as there is now different types of budget exceed checks that are managed directly in budget module.
Also, the check is now more of an informative message than a blocking error.

* Tax rate: Allow to define the tax rate in % instead of a coefficient.
* Bank details : change how full name is computed

Bank details full name is now computed as :
`<code> - <label> - <iban> - <bank.fullname>`

* Sequence: display an understandable message when the generated sequence value already exists
* Move/Journal: add a prefix on the origin when we reverse or copy a move.
* Accounting Situation: add a search bar on the move line dashlet.
* Account Configuration: in configuration by company, split the configuration to activate payment vouchers on invoice to allow to configure independently payment vouchers on supplier and on customer invoices.
* Invoice report: add text line option on deliveries under tax table in invoice report.
* Bank order line origin: add new button to open the invoice pdf files.
* App: add a new option allowing to install apps automatically on startup with demo data

`aos.apps.install-apps` property can now be used to install AOS modules by default when starting Axelor Open Suite on a new database. If `data.import.demo-data` is true, then demo data will also be imported.

* Move: add a coherence control with tax lines

When you want to validate a move, a coherence control now checks if tax lines are duplicated with the same taxline and the same vat system.

* Employee: change employee card view.
* Move: add reverse charge move line generation on auto tax generation.
* Partner: add validity check on registration code.
* Fixed asset: improve the split feature by adding the possibility to split by gross value.
* Global tracking log: Add reference display button.
* FTP Management: Added a generic connector for file transfer (only support SFTP for now).
* Contract batch: Add invoicing date for invoicing contract batch.
* Move: add a new field company bank details used in forecast recap.
* Move: add button to mass reverse move from grid view.
* Reconcile manager: add new functionality reconcile manager in accounting periodic menu

This feature allows to filter with parameters on move lines with mass reconcile or unreconcile function

* Move: Add more coherence control to check if tax fields should be filled.
* Contract batch: Add type for invoicing contract batch

Added a selection field to be able to run the contract invoicing batch for supplier or customer contracts only

* Payment mode: Add a triggering parameter for the generation of accounting moves in the payment mode.

Moves may be generated immediately (current behavior) or cannot be generated automatically. Moreover, if the bank payment application is activated, it is also possible to generate moves at the bank order confirmation, bank order validation or bank order realization.

* Stock Batch: add a batch to recompute all quantities and WAP history in stock location lines. In WAP history, removed link to stock move line.
* Contact: Improve contact card view presentation.

#### Fixed

* Accounting move: fix how partner information is managed on accounting moves

In the accounting move header, if the partner is filled, then the partner column in lines is hidden. If it is empty, then we allow different partners on move lines.
On FEC import, the partner header on created moves is not filled anymore.
An error on move validation is now raised if the header partner is different from the one in its lines.

#### Removed

* Remove stock and production activation for the mobile application.

A new mobile application for stock and production modules are now available, these modules on the old application are no longer maintained.

* Account budget: Remove checkAvailableBudget in budget, which was unused.
* Accounting report: removed old specific export format for Sale, Purchase, Treasury, Refund (1006 to 1009 accounting report type). Already replaced per the generic Journal entry export with a filter on the journal.

[6.4.5]: https://github.com/axelor/axelor-open-suite/compare/v6.4.4...v6.4.5
[6.4.4]: https://github.com/axelor/axelor-open-suite/compare/v6.4.3...v6.4.4
[6.4.3]: https://github.com/axelor/axelor-open-suite/compare/v6.4.2...v6.4.3
[6.4.2]: https://github.com/axelor/axelor-open-suite/compare/v6.4.1...v6.4.2
[6.4.1]: https://github.com/axelor/axelor-open-suite/compare/v6.4.0...v6.4.1
[6.4.0]: https://github.com/axelor/axelor-open-suite/compare/v6.3.5...v6.4.0
