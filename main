import sys
from datetime import datetime, timedelta

def main(lines):
    # このコードは標準入力と標準出力を用いたサンプルコードです。
    # このコードは好きなように編集・削除してもらって構いません。
    # ---
    # This is a sample code to use stdin and stdout.
    # Edit and remove this code as you like.
    reserve_ID = []
    # reserve_ID_index = 500
    final_results = []

    def get_cases(n):
        cases = []
        for i in range(n): 
            cases.append(lines[i + 1])
        return cases
    def get_options(num_of_opt, index):
        id_options = int(index + 1) 
        options = []
        for i in range(int(num_of_opt)):
            # print("id_opton", id_options, lines[id_options].split())
            options.append({
                        "option_id": lines[id_options].split()[0],
                        "option_time_required": lines[id_options].split()[1],
                        "option_cost": lines[id_options].split()[2]})
            id_options += 1
        return options
    def get_venue_info(num_of_venue, index_of_num_venue): #
        global index_of_events
        venue_info = []
        # venue_info_form = {
        #     "x",
        #     "y", 
        #     "capacity",
        #     "open",
        #     "close",
        #     "time_required_a", 
        #     "time_required_b", 
        #     "cost_a", 
        #     "cost_b",
        #     "option_info": [{
        #         "option_id",
        #         "option_time_required",
        #         "option_cost"}]
        #      "num_of_events",
        #      "events": [{}],
        # }
        global index_of_events
        n = int(index_of_num_venue)  
        # print("index_of_num_venue", index_of_num_venue) 
        for i in range(int(num_of_venue)):
            venue_info.append(
                {
                    "venue_ID": i+1,
                    "x": lines[n+1].split()[0],
                    "y": lines[n+1].split()[1],
                    "capacity": lines[n+1].split()[2],
                    "open": lines[n+1].split()[3],
                    "close": lines[n+1].split()[4],
                    "available_time": make_time_in_float(lines[n+1].split()[3], lines[n+1].split()[4], lines[n+1].split()[2]),
                    "time_required_a": lines[n+2].split()[0], 
                    "time_required_b": lines[n+2].split()[1], 
                    "cost_a": lines[n+2].split()[2], 
                    "cost_b": lines[n+2].split()[3],
                    "k": lines[n+3],
                    "option_info": get_options(lines[n+3], n+3)
                }
            )
            n +=  (2 + int(lines[n+3]) + 1)  
            index_of_events = n
            # print("n", n, index_of_events)
        return venue_info
            # return venue_info.update["general_info"] = []
    def make_time_in_float(start, close, capacity):
        # Start and end times
        start_time = datetime.strptime(start, "%H:%M:%S")
        end_time = datetime.strptime(close, "%H:%M:%S")

        # Time increment (30 minutes)
        increment = timedelta(minutes=30)

        # List to hold available times
        available_times = []

        # Generate times from start to end with 30-minute increments
        current_time = start_time
        while current_time <= end_time:
            for i in range(int(capacity)):
                available_times.append(current_time.strftime("%H:%M:%S"))
            current_time += increment
        return available_times

    def get_events(index):
        events = []
        # print("get_events", index)
        for i in range(int(lines[index])):
            events.append(lines[index + i + 1])
        return events

    n = int(lines[0]) #test_cases age restrict
    index_of_num_venue = int(n) + 1
    num_of_venue = int(lines[index_of_num_venue]) #number of avaiable venues

    query = {
        "number of cases": n,
        "cases": get_cases(n),
        "available_venues": num_of_venue,
        "venue_info": get_venue_info(num_of_venue, index_of_num_venue),
        "num_of_events": lines[index_of_events + 1],
        "events": get_events(index_of_events + 1)

    }
    # print("jkj", query)

    def reservation_actions(k = query["events"]):
        activity=[]
        for i in range(len(k)):
            activity.append(k[i].split())
        # print("activity", activity)
        return activity

    def check_age_for_option(num_of_options, optionIDs, age):
        print("check_age_for_option", optionIDs, num_of_options)
        if int(num_of_options) != 0:
            if not query["cases"][0]:
                raise ValueError
            else: 
                for i in range(len(optionIDs)):
                    age_range = query["cases"][int(optionIDs[i]) - 1].split()
                    # print("age", age_range, int(age_range[0])<= int(age) <= int(age_range[1]))
                    return (int(age_range[0])<= int(age) <= int(age_range[1]))
                        # return True
                    
            # else: 
            #     return [False, "reserve: inapplicable age"]
    def is_30_minute_increment(time_str, datetime_reserve, date_time_obj):
    # Split the time string into hours, minutes, and seconds
        # print("time", str(time_str).split(':'))
        book_date = datetime.strptime(datetime_reserve, "%Y/%m/%d-%H:%M:%S")
        if not book_date > date_time_obj:
            parts = str(time_str).split(':')
            hours, minutes, seconds = parts
        # if len(parts) != 3:
        #     return False
    # Convert the minutes to an integer and check if it's either 00 or 30
            if minutes in ['00', '30']: 
                return True
    
    def check_available_venue(id_v):
        if query["venue_info"][int(id_v) -1]:
            return True
        else:
            return False

    def check_available_time(id_v,reserve_time, time):
        open_time = query["venue_info"][int(id_v) -1]["open"]
        close_time = query["venue_info"][int(id_v) -1]["close"]
        start_time = datetime.strptime(str(open_time), "%H:%M:%S")
        end_time = datetime.strptime(str(close_time), "%H:%M:%S")
        # business_time  = make_time_in_float(open_time, close_time, 1)
        # new_time = datetime.strptime(str(reserve_time), '%H:%M:%S')
        # time = datetime.strptime(str(time), "%H:%M:%S")
        # print("cheifcjosif", str(reserve_time) in business_time) 
        # if (time > 30):
                # print("new here", time)
                    # new_time = reserve_time + timedelta(minutes=30)
        time_obj = datetime.strptime(str(reserve_time), '%H:%M:%S')
        new_time = time_obj + timedelta(minutes=time)
                    # print("true time", time_slots, new_time.strftime("%H:%M:%S"))
                    # time_slots.pop(time_slots.index(str(new_time.strftime("%H:%M:%S"))))
        if start_time <= new_time <= end_time:
            return True
        # else:
        #     return [False, "reserve: non-business hour"]
    
    def check_compatible_site(id_v, plan, num_of_options, option_ids):
        print("check_compatible_site")
        def is_list_in_list(main_list, subset):
            return all(item in main_list for item in subset)
        venue_options = [x['option_id'] for x in query["venue_info"][int(id_v) -1]["option_info"]]
        # print("venue options", venue_options)
        if plan == 'A' or 'B':
            if is_list_in_list(venue_options, option_ids):
                return True
        #     else:
        #         return [False, "reserve: incompatible site"]
        # else:
        #     return [False, "reserve: incompatible site"]
    
    def check_capacity_available(id_v,reserve_time, time):
        time_slots = query["venue_info"][int(id_v) -1]["available_time"]
        print("check_capacity_available", time_slots)
        # print("update", query["venue_info"][int(id_v) -1]["available_time"])
        
        if str(reserve_time) in time_slots:
            # print("truefsdfadf", time_slots)
            time_slots.pop(time_slots.index(str(reserve_time)))
            if (time > 30):
                print("new here", time)
                for i in range(time//30):
                    # new_time = reserve_time + timedelta(minutes=30)
                    time_obj = datetime.strptime(str(reserve_time), '%H:%M:%S')
                    new_time = time_obj + timedelta(minutes=30)
                    # print("true time", time_slots, new_time.strftime("%H:%M:%S"))
                    time_slots.pop(time_slots.index(str(new_time.strftime("%H:%M:%S"))))
                    print("end")
            return True
        # else:
        #     return [False, "reserve: fully reserved"]

        # if query["venue_info"][int(id_v) -1]["available time"]
    # venue_options = [x['option_id'] for x in query["venue_info"][int(1) -1]["option_info"]]
    # print("venue options", venue_options)

    def check_all(venue_to_reserve, reserve_time, num_of_options, plan, option_ids, age, time, datetime_reserve, date_time_obj):
        # check_list = []
        if check_available_venue(venue_to_reserve): 
            if not is_30_minute_increment(reserve_time, datetime_reserve, date_time_obj):
                print("reached")
                return [False, "reserve: invalid starting datetime"]
            if not check_available_time(venue_to_reserve, reserve_time, time):
                print("reached biz")
                return [False, "reserve: non-business hour"]
            if int(num_of_options) != 0:
                if not check_age_for_option(num_of_options, option_ids, age):
                    print("reached biz4")
                    return [False, "reserve: inapplicable age"]
            if not check_compatible_site(venue_to_reserve, num_of_options, plan, option_ids):
                print("reached biz3")
                return [False, "reserve: incompatible site"]
            if not check_capacity_available(venue_to_reserve, reserve_time, time):
                print("reached biz2")
                return [False, "reserve: fully reserved"]
            return True
        else:
            raise ValueError

    def do_reserve(reserve_event, reserve_ID_index):
        datetime_reserve = reserve_event[1]
        userID = reserve_event[2]
        age = reserve_event[3]
        venue_to_reserve = reserve_event[4] #id of venue
        date_time_obj = datetime.strptime(reserve_event[5], "%Y/%m/%d-%H:%M:%S")
        reserve_date = date_time_obj.date()
        reserve_time = date_time_obj.time()
        # print("reserve_date", query["venue_info"][int(venue_to_reserve) -1]["time_required_a"])
        # print("dfjashdfj", str(reserve_time) in query["venue_info"][int(venue_to_reserve) -1]["available time"])
        plan = reserve_event[6]
        num_of_options = reserve_event[7]
        print("num", userID)
        option_ids = [x for x in reserve_event[8:]] 
        price = int(query["venue_info"][int(venue_to_reserve) -1]["cost_a"]) if plan == 'A' else int(query["venue_info"][int(venue_to_reserve) -1]["cost_b"])
        time = int(query["venue_info"][int(venue_to_reserve) -1]["time_required_a"]) if plan == 'A' else int(query["venue_info"][int(venue_to_reserve) -1]["time_required_b"])
        if not query["venue_info"][int(venue_to_reserve) -1]:
            print("erroe")
            raise ValueError
        else: 
            # if is_30_minute_increment(reserve_time):
                # print("iiidfjksfdilsd", len(option_ids))
            if (int(num_of_options) != 0): 
                for i in range(int(num_of_options)):
                    print("check_reservation_match", price, time)
                    price += int(query["venue_info"][int(venue_to_reserve) - 1]["option_info"][i -1]["option_cost"])
                    time += int(query["venue_info"][int(venue_to_reserve) -1]["option_info"][i - 1]["option_time_required"])
            print("time", int(query["venue_info"][int(venue_to_reserve) -1]["cost_a"]), price)
            check_reservation_match = check_all(venue_to_reserve, reserve_time, num_of_options, plan, option_ids, age, time, datetime_reserve, date_time_obj)
            if check_reservation_match == True:
                # print("iii")   
                return [1, ("reserve: " + str(reserve_ID_index) + " " + str(time) + " " + str(price))]
            else:
                return check_reservation_match

    def get_closest_to_farthest(ref_x, ref_y, locations):
        print("get_closest_to_farthest", locations)
     # Calculate distances for each location
        distances = []
        for location in locations:
            venue_ID, current_x, current_y = location
            distance = ((int(ref_x) - int(current_x)) ** 2 + (int(ref_y) - int(current_y)) ** 2) ** 0.5
            distances.append(distance)

  # Sort locations based on distances (ascending order)
            sorted_locations = sorted(zip(locations, distances))

  # Return the list of locations from the sorted list
        print("distance", distances)
        return [location for location, _ in sorted_locations]


    def get_XY_list(num_of_venue):
        lsit_XY = []
        for i in range(int(num_of_venue)):
            lsit_XY.append([query["venue_info"][i]["venue_ID"], query["venue_info"][i]["x"], query["venue_info"][i]["y"]])
        return lsit_XY

    def get_available(all_events):
        date_time = all_events[1]
        user_x = all_events[2]
        user_y = all_events[3]
        reservation_date = all_events[4]
        diagnpstic_plan = all_events[5]
        option_info = all_events[6]
        option_ids = [x for x in all_events[7:]]
        available_venue = []
        num_of_venue = query["available_venues"]
        venue_location = get_XY_list(num_of_venue)
        # print("venue_location", venue_location, query["venue_info"][0]["available_time"])
        closest_location_venue_ID = get_closest_to_farthest(user_x, user_y, venue_location)
        # print("locatoin", closest_location_venue_ID[0][0])
        for i in range(int(num_of_venue)):
            available_time = query["venue_info"][int(closest_location_venue_ID[i][0]) - 1]["available_time"]
            site_ID = query["venue_info"][closest_location_venue_ID[i][0] - 1]["venue_ID"]
            for k, j in enumerate(available_time):
                if k == 0:
                    available_venue.append("site ID = "+ str(site_ID) + ", reservation slot = " + str(j))
                if k > 0:
                    if (j != available_time[k-1]):
                        available_venue.append("site ID = "+ str(site_ID) + ", reservation slot = " + str(j)) 
        # print("available_venue", available_venue)
        return available_venue

    # delete = query["venue_info"][1]["available_time"].remove('13:00:00')
    # newQu = query["venue_info"][1]["available_time"]
    # print("query", newQu)
    try: 
        all_events = reservation_actions()
        reserve_ID_index = 1
        # print("length event", len(all_events))
        for i in range(int(query["num_of_events"])): 
            # for j in range(len(all_events[i])):
            # print("event", i, all_events[i][0])
            if all_events[i][0] == 'reserve:':
                reserve_add = do_reserve(all_events[i], reserve_ID_index)
                # print("items", final_results, all_events[i][0])
                final_results.append(reserve_add[1])
                if reserve_add[0] == 1:
                    reserve_ID_index += 1
                # reserve_ID_index == reserve_ID_index + 1 if reserve_add[0] == 1 else reserve_ID_index = reserve_ID_index
                # print("reserve_ID_index???", query["venue_info"][0]["available_time"])
            elif all_events[i][0] == 'get-available:':
                get_available_all = get_available(all_events[i])
                final_results.append(len(get_available_all))
                final_results = final_results + get_available_all
            else:
                final_results.append(None)
                # return final_results 
            print("temporary", final_results)           
        for item in final_results:
            print(item)
        # print("kdmv", reserve_ID_index)
    except ValueError:
        print("Error Occured")



if __name__ == '__main__':
    lines = []
    for l in sys.stdin:
        lines.append(l.rstrip('\r\n'))
    main(lines)
