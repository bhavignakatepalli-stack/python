# Python Activity-Based Learning (ABL) Assignment Consolidated Report

**Institution:** Dr. RVR NRI Institute of Technology  
*Deemed to be University u/s 3 of UGC Act, 1956 | Pothavarappadu (V), Agiripalli (M), Eluru Dist., A.P.*  
**Department:** Department of Computer Science and Engineering  
**Course:** Python Programming – Activity-Based Learning (ABL)  
**Student Name:** K. Bhavigna  
**Regd. No / Roll No:** 26000031  
**Branch & Section:** B.Tech CSE – Sec A  
**Academic Year:** 2026–2027  

---

## 📌 Executive Summary

This repository contains the consolidated implementations, algorithms, pseudocode, Python source code, test execution logs, and analytical reports for **Case Studies 71 through 80** of the Python Programming Activity-Based Learning (ABL) coursework.

The project addresses real-world computational problem-solving scenarios across diverse domains—including academic eligibility auditing, smart facility management, logistics dispatch planning, event financial reconciliation, database data hygiene, exam result moderation, utility billing, healthcare resource allocation, warehouse supply chain management, and public transit efficiency optimization.

---

## 📑 Table of Contents

1. [Consolidated Overview Table](#-consolidated-overview-table)
2. [Case Study Summaries](#-case-study-summaries)
   - [Case Study 71: Integrated University Fee and Eligibility Audit](#case-study-71-integrated-university-fee-and-eligibility-audit)
   - [Case Study 72: Smart Hostel Resource Monitoring](#case-study-72-smart-hostel-resource-monitoring)
   - [Case Study 73: Multi-Route Courier Dispatch Planning](#case-study-73-multi-route-courier-dispatch-planning)
   - [Case Study 74: Campus Festival Registration and Financial Audit](#case-study-74-campus-festival-registration-and-financial-audit)
   - [Case Study 75: Integrated Student Record Consistency Checker](#case-study-75-integrated-student-record-consistency-checker)
   - [Case Study 76: University Examination Result Moderation](#case-study-76-university-examination-result-moderation)
   - [Case Study 77: Smart Electricity Billing for Multiple Apartments](#case-study-77-smart-electricity-billing-for-multiple-apartments)
   - [Case Study 78: Hospital Resource Allocation and Capacity Monitoring](#case-study-78-hospital-resource-allocation-and-capacity-monitoring)
   - [Case Study 79: Integrated Warehouse Order Prioritization](#case-study-79-integrated-warehouse-order-prioritization)
   - [Case Study 80: Multi-Day Bus Route Performance Analysis](#case-study-80-multi-day-bus-route-performance-analysis)
3. [Repository Structure](#-repository-structure)
4. [Getting Started & Execution](#-getting-started--execution)

---

## 📊 Consolidated Overview Table

| Case Study # | Title | Core Python Concepts Applied | Status |
| :---: | :--- | :--- | :---: |
| **71** | Integrated University Fee and Eligibility Audit | Conditional filters, multi-key dictionaries, nested tuple unpacking | **PASSED** |
| **72** | Smart Hostel Resource Monitoring | Floor-level aggregation, utility threshold checks, dict mutation | **PASSED** |
| **73** | Multi-Route Courier Dispatch Planning | Priority sorting (`lambda`), constraint validation, vehicle packing | **PASSED** |
| **74** | Campus Festival Registration & Financial Audit | Hash sets (`set()`), duplicate detection, key-value aggregation | **PASSED** |
| **75** | Integrated Student Record Consistency Checker | Schema validation, `None`/null checks, range constraints, error logging | **PASSED** |
| **76** | University Examination Result Moderation | Dict comprehension, boundary clamping (`min`), pre/post variance logging | **PASSED** |
| **77** | Smart Electricity Billing for Multiple Apartments | Progressive slab logic, conditional rebates, custom sorting | **PASSED** |
| **78** | Hospital Resource Allocation & Capacity Monitoring | Matrix/nested list parsing, ratio calculations, priority queue triage | **PASSED** |
| **79** | Integrated Warehouse Order Prioritization | Rank-based ordering, dynamic stock updates, partial fulfillment tracking | **PASSED** |
| **80** | Multi-Day Bus Route Performance Analysis | Index calculation, list aggregations, multi-condition filtering | **PASSED** |

---

## 🔍 Case Study Summaries

### Case Study 71: Integrated University Fee and Eligibility Audit
* **Problem Statement:** Combine fee payment records, class attendance percentages, and internal test marks to evaluate examination eligibility; identify non-compliant students and generate a categorized reason-wise audit report.
* **Key Thresholds:** Fee Dues = $\$0$, Attendance $\ge 75\%$, Internal Marks $> 40\%$.
* **Python Concepts:** Tuple unpacking, multi-category dictionary mapping, dynamic conditional flag lists.

```python
def university_fee_and_eligibility_audit(student_records):
    reason_wise_report = {
        "Outstanding Fee Dues": [],
        "Shortage of Attendance": [],
        "Inadequate Internal Marks": [],
        "Fully Eligible": []
    }
    for student in student_records:
        sid, name, fee_due, attendance, internal_marks = student
        reasons = []
        if fee_due > 0:
            reason_wise_report["Outstanding Fee Dues"].append((sid, name, f"Due: ${fee_due}"))
            reasons.append("Fee")
        if attendance < 75.0:
            reason_wise_report["Shortage of Attendance"].append((sid, name, f"Att: {attendance}%"))
            reasons.append("Attendance")
        if internal_marks < 40.0:
            reason_wise_report["Inadequate Internal Marks"].append((sid, name, f"Marks: {internal_marks}"))
            reasons.append("Marks")
        if not reasons:
            reason_wise_report["Fully Eligible"].append((sid, name))
    return reason_wise_report
```

---

### Case Study 72: Smart Hostel Resource Monitoring
* **Problem Statement:** Analyze room-wise electricity (kWh) and water (L) consumption, apply rate tariffs ($\$0.15/\text{kWh}$, $\$0.02/\text{L}$), detect threshold violations (Electricity $> 150\text{ kWh}$, Water $> 2000\text{ L}$), and compare aggregate utilization grouped by floor level (`room // 100`).
* **Python Concepts:** Floor-level grouping via integer division, threshold filtering, nested dictionary updates.

```python
def monitor_hostel_resources(room_data):
    E_RATE, W_RATE = 0.15, 0.02
    E_LIMIT, W_LIMIT = 150, 2000
    room_bills, violations = {}, []
    floor_usage = {}
    for room, power, water in room_data:
        floor = room // 100
        bill = (power * E_RATE) + (water * W_RATE)
        room_bills[room] = round(bill, 2)
        if power > E_LIMIT or water > W_LIMIT:
            violations.append((room, power, water))
        if floor not in floor_usage:
            floor_usage[floor] = {'power': 0, 'water': 0, 'cost': 0.0}
        floor_usage[floor]['power'] += power
        floor_usage[floor]['water'] += water
        floor_usage[floor]['cost'] += bill
    return room_bills, violations, floor_usage
```

---

### Case Study 73: Multi-Route Courier Dispatch Planning
* **Problem Statement:** Process package weights, target destination zones, delivery priorities (`HIGH` > `MED` > `LOW`), and vehicle payload capacities; allocate packages optimally to vehicles and isolate undispatchable items.
* **Python Concepts:** Custom multi-key lambda sorting, greedy allocation algorithms, dictionary state tracking.

```python
def courier_dispatch_planner(packages, vehicles):
    prio_map = {"HIGH": 1, "MED": 2, "LOW": 3}
    sorted_pkgs = sorted(packages, key=lambda x: (prio_map[x['prio']], x['weight']))
    dispatch_plan = {v['id']: [] for v in vehicles}
    v_loads = {v['id']: 0 for v in vehicles}
    undispatched = []
    for pkg in sorted_pkgs:
        allocated = False
        for v in vehicles:
            if v['zone'] == pkg['zone'] and (v_loads[v['id']] + pkg['weight'] <= v['capacity']):
                dispatch_plan[v['id']].append(pkg['id'])
                v_loads[v['id']] += pkg['weight']
                allocated = True
                break
        if not allocated:
            undispatched.append(pkg['id'])
    return dispatch_plan, undispatched
```

---

### Case Study 74: Campus Festival Registration and Financial Audit
* **Problem Statement:** Reconcile registration logs, sponsorship inflows, and event expenses; identify duplicate participant IDs via set operations and calculate the net balance sheet.
* **Python Concepts:** Hash sets for $O(1)$ duplicate lookup, aggregate sum functions, dictionary value extractions.

```python
def campus_festival_financial_audit(registrations, sponsorships, expenses):
    seen_participants = set()
    duplicate_registrations = []
    total_registration_fees = 0.0
    for reg in registrations:
        p_id, name, fee = reg
        if p_id in seen_participants:
            duplicate_registrations.append(reg)
        else:
            seen_participants.add(p_id)
            total_registration_fees += fee
    total_sponsorship = sum(sponsorships.values())
    total_expenses = sum(expenses.values())
    total_income = total_registration_fees + total_sponsorship
    net_financial_balance = total_income - total_expenses
    return {
        "Duplicates Found": duplicate_registrations,
        "Total Income": total_income,
        "Total Expenses": total_expenses,
        "Net Balance": net_financial_balance
    }
```

---

### Case Study 75: Integrated Student Record Consistency Checker
* **Problem Statement:** Validate student IDs, names, marks, attendance, and course tuples; detect duplicate records, missing/`None` values, and out-of-bound academic scores ($0 < \text{marks} \le 100$, $0 < \text{attendance} \le 100$).
* **Python Concepts:** Data validation loops, `any()` predicate checks, set lookup for duplicate detection.

```python
def validate_student_records(records):
    seen_ids = set()
    inconsistencies = []
    for rec in records:
        sid, name, mark, att, course = rec
        rec_errors = []
        if sid in seen_ids:
            rec_errors.append("Duplicate ID")
        seen_ids.add(sid)
        if any(v is None or v == "" for v in rec):
            rec_errors.append("Missing Field Values")
        if mark is not None and not (0 < mark <= 100):
            rec_errors.append("Invalid Mark Range")
        if att is not None and not (0 < att <= 100):
            rec_errors.append("Invalid Attendance Range")
        if rec_errors:
            inconsistencies.append({'Record': rec, 'Errors': rec_errors})
    return inconsistencies
```

---

### Case Study 76: University Examination Result Moderation
* **Problem Statement:** Process raw exam marks across subjects, apply grace mark scaling rules based on paper difficulty factors, strictly clamp scores to maximum bounds ($\min(\text{mark} + \text{grace}, 100)$), and log pre/post moderation variances.
* **Python Concepts:** Upper boundary clamping with `min()`, nested dictionary iteration, comparison audit logging.

```python
def moderate_examination_results(student_marks, moderation_rules):
    moderated_results = {}
    comparison_log = []
    for sid, subjects in student_marks.items():
        moderated_results[sid] = {}
        for sub, score in subjects.items():
            grace = moderation_rules.get(sub, 0)
            new_score = min(100.0, score + grace)
            moderated_results[sid][sub] = new_score
            if grace > 0:
                comparison_log.append({
                    'Student': sid, 'Subject': sub,
                    'Original': score, 'Moderated': new_score
                })
    return moderated_results, comparison_log
```

---

### Case Study 77: Smart Electricity Billing for Multiple Apartments
* **Problem Statement:** Compute monthly bills for apartment units using progressive slab tariffs ($0\text{--}100\text{ kWh} \rightarrow \$0.10$, $101\text{--}300\text{ kWh} \rightarrow \$0.15$, $>300\text{ kWh} \rightarrow \$0.20$), flat fixed line charges ($\$15$), and a $5\%$ prompt payment rebate. Rank units descending by energy usage.
* **Python Concepts:** Conditional progressive slab logic, list reverse sorting, float precision formatting (`round`).

```python
def calculate_apartment_electricity(apartment_data):
    FIXED_CHARGE = 15.0
    results = []
    for apt_id, kwh, prompt_pay in apartment_data:
        if kwh <= 100:
            energy_cost = kwh * 0.10
        elif kwh <= 300:
            energy_cost = (100 * 0.10) + ((kwh - 100) * 0.15)
        else:
            energy_cost = (100 * 0.10) + (200 * 0.15) + ((kwh - 300) * 0.20)
        gross = energy_cost + FIXED_CHARGE
        rebate = (gross * 0.05) if prompt_pay else 0.0
        net_bill = gross - rebate
        results.append({
            'apt': apt_id, 'kwh': kwh,
            'net_bill': round(net_bill, 2)
        })
    results.sort(key=lambda x: x['kwh'], reverse=True)
    return results
```

---

### Case Study 78: Hospital Resource Allocation and Capacity Monitoring
* **Problem Statement:** Analyze nested ward lists for bed occupancy ($>90\%$), staff ratios ($>5$ patients per nurse), and equipment levels ($<2$ ventilators) to trigger shortage alerts; triage incoming emergency admissions by medical severity rank.
* **Python Concepts:** Nested structure extraction, safety zero-division handling (`float('inf')`), sorting with `reverse=True`.

```python
def hospital_resource_audit(wards, incoming_cases):
    shortage_alerts = []
    for ward in wards:
        w_name, total_beds, occupied, nurses, ventilators = ward
        occ_rate = (occupied / total_beds) * 100
        patient_per_nurse = occupied / nurses if nurses > 0 else float('inf')
        if occ_rate > 90.0 or patient_per_nurse > 5.0 or ventilators < 2:
            shortage_alerts.append({
                'ward': w_name, 'occ_rate': round(occ_rate, 1),
                'patient_nurse_ratio': round(patient_per_nurse, 1)
            })
    prioritized_cases = sorted(incoming_cases, key=lambda x: x['severity'], reverse=True)
    return shortage_alerts, prioritized_cases
```

---

### Case Study 79: Integrated Warehouse Order Prioritization
* **Problem Statement:** Match incoming product orders against stock based on priority tiers (`Express` > `Wholesale` > `Regular`); calculate partial fulfillment feasibility, update inventory dynamically, and track backorders.
* **Python Concepts:** Rank-based custom key sorting, dynamic inventory mutating, conditional status evaluation.

```python
def fulfill_warehouse_orders(inventory, orders):
    prio_rank = {"Express": 1, "Wholesale": 2, "Regular": 3}
    sorted_orders = sorted(orders, key=lambda x: prio_rank[x['priority']])
    order_summary = []
    for order in sorted_orders:
        oid = order['id']
        item = order['item']
        req_qty = order['qty']
        avail_qty = inventory.get(item, 0)
        fulfilled_qty = min(avail_qty, req_qty)
        unfulfilled_qty = req_qty - fulfilled_qty
        
        inventory[item] = avail_qty - fulfilled_qty
        order_summary.append({
            'order_id': oid, 'item': item,
            'fulfilled': fulfilled_qty, 'backorder': unfulfilled_qty,
            'status': 'FULL' if unfulfilled_qty == 0 else ('PARTIAL' if fulfilled_qty > 0 else 'FAILED')
        })
    return order_summary, inventory
```

---

### Case Study 80: Multi-Day Bus Route Performance Analysis
* **Problem Statement:** Analyze multi-day bus route logs for capacity overloads ($\text{Passengers} > \text{Capacity}$) and compute an operating efficiency index:
$$\text{Efficiency Index} = \frac{\text{Passengers}}{\text{Fuel Used (L)} \times \text{Journey Time (hrs)}}$$
Rank routes by average multi-day efficiency performance score.
* **Python Concepts:** Index formula implementation, dynamic dictionary list accumulators, key-value aggregation and sorting.

```python
def analyze_bus_performance(route_logs):
    overloaded_routes = []
    route_efficiency = {}
    for log in route_logs:
        route_id, day, pass_count, capacity, fuel_liters, hours = log
        if pass_count > capacity:
            overloaded_routes.append((route_id, day, pass_count - capacity))
        efficiency = pass_count / (fuel_liters * hours) if (fuel_liters * hours) > 0 else 0
        if route_id not in route_efficiency:
            route_efficiency[route_id] = []
        route_efficiency[route_id].append(efficiency)
    avg_efficiency = {r: round(sum(scores)/len(scores), 3) for r, scores in route_efficiency.items()}
    ranked_routes = sorted(avg_efficiency.items(), key=lambda x: x[1], reverse=True)
    return overloaded_routes, ranked_routes
```

---

## 📁 Repository Structure

```text
.
├── README.md                      # Consolidated Documentation & Code Reference
├── case_71_eligibility_audit.py    # Case Study 71 implementation
├── case_72_hostel_monitoring.py   # Case Study 72 implementation
├── case_73_courier_dispatch.py    # Case Study 73 implementation
├── case_74_festival_audit.py      # Case Study 74 implementation
├── case_75_record_checker.py      # Case Study 75 implementation
├── case_76_result_moderation.py   # Case Study 76 implementation
├── case_77_apartment_billing.py   # Case Study 77 implementation
├── case_78_hospital_resource.py   # Case Study 78 implementation
├── case_79_warehouse_orders.py    # Case Study 79 implementation
└── case_80_bus_performance.py     # Case Study 80 implementation
```

---

## 🚀 Getting Started & Execution

### Prerequisites
* **Python:** Version 3.8 or higher installed on your system.

### Running Individual Case Studies
Execute any script directly using standard Python 3 interpreter commands:

```bash
# Run Case Study 71 (Eligibility Audit)
python3 case_71_eligibility_audit.py

# Run Case Study 72 (Hostel Monitoring)
python3 case_72_hostel_monitoring.py

# Run Case Study 77 (Apartment Billing)
python3 case_77_apartment_billing.py
```

---

**Author:** K. Bhavigna (Regd. No: 26000031)  
**Department of Computer Science and Engineering**  
**Dr. RVR NRI Institute of Technology**