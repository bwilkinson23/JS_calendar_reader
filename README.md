# JS_calendar_reader

This program is designed to display the opening / closing hours for the library dynamically. That is, the opening and closing hours will correspond to the current date. If the library is closed, the displayed text will read "Currently closed. See Library Hours." In both cases (case 1: library is open; case 2: library is closed), the text will be a hyperlink that takes the user to a more detailed calendar.

In this code, events[0].end.dateTime and events[0].start.dateTime yields the ending and starting (respectively) time and date of the first event in the following format: YYYY-MM-DDTHH:MM:SS-XX:XX where XX:XX is the time zone. (e.g., 2017-03-07T21:00:00-08:00).

The date/time yielded in this way is altered in a few ways. 1.) there is a conversion from military time to civillian time (assigned varaible "cTime"), leading 0s are dropped and am or pm is added appropriately.

Testing oracle:

#####################################################################################################
##     if today's hours are:  ||     events[0].end.dateTime   ||     final output:               #### 
##                            ||     evemts[0].start.dateTime ||                                 ####
##-----------------------------------------------------------------------------------------------####
##       7:30am - 9:00pm      ||   2017-03-07T21:00:00-08:00  ||  Today's Hours: 7:30am-9:00pm   ####
##                            ||   2017-03-07T07:30:00-08:00  ||                                 ####
##-----------------------------------------------------------------------------------------------####
##       11:00am - 4:00pm     ||   2017-03-07T11:00:00-08:00  ||  Today's Hours: 7:30am-9:00pm   ####
##                            ||   2017-03-07T16:00:00-08:00  ||                                 ####
##-----------------------------------------------------------------------------------------------####
##        closed              || *some date other than today* ||      Currently closed.          #### 
##                                                                    See Libarary Hours         ####
#####################################################################################################

*This final output excludes the <a href></a> tags that are added around the text*
