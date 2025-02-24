NAME
    Games::Dice - Perl module to simulate die rolls

VERSION
    version 0.046

SYNOPSIS
      use Games::Dice 'roll';
      $strength = roll '3d6+1';

      use Games::Dice 'roll_array';
      @rolls = roll_array '4d8';

DESCRIPTION
    Games::Dice simulates die rolls. It uses a function-oriented (not
    object-oriented) interface. No functions are exported by default. At
    present, there are two functions which are exportable: "roll" and
    "roll_array". The latter is used internally by "roll", but can also be
    exported by itself.

    The number and type of dice to roll is given in a style which should be
    familiar to players of popular role-playing games: *a*d*b*[+-*/b]*c*.
    *a* is optional and defaults to 1; it gives the number of dice to roll.
    *b* indicates the number of sides to each die; the most common,
    cube-shaped die is thus a d6. % can be used instead of 100 for *b*;
    hence, rolling 2d% and 2d100 is equivalent. If F is used for *b* fudge
    dice are used, which either results in -1, 0 or 1. "roll" simulates *a*
    rolls of *b*-sided dice and adds together the results. The optional end,
    consisting of one of +-*/b and a number *c*, can modify the sum of the
    individual dice. +-*/ are similar in that they take the sum of the rolls
    and add or subtract *c*, or multiply or divide the sum by *c*. (x can
    also be used instead of *.) Hence, 1d6+2 gives a number in the range
    3..8, and 2d4*10 gives a number in the range 20..80. (Using / truncates
    the result to an int after dividing.) Using b in this slot is a little
    different: it's short for "best" and indicates "roll a number of dice,
    but add together only the best few". For example, 5d6b3 rolls five six-
    sided dice and adds together the three best rolls. This is sometimes
    used, for example, in role-playing to give higher averages. Likewise
    using 'w' in this slot is short for "worst" and indicates "roll a number
    of dice, but add together only the worst few". For example 2d20w1 rolls
    two twenty-sided dice and returns the worst (lower) of the two rolls.
    This is sometimes used in role playing games to do a "roll with
    disadvantage" where you roll twice and take the lower of the two rolls.

    Generally, "roll" probably provides the nicer interface, since it does
    the adding up itself. However, in some situations one may wish to
    process the individual rolls (for example, I am told that in the game
    Feng Shui, the number of dice to be rolled cannot be determined in
    advance but depends on whether any 6s were rolled); in such a case, one
    can use "roll_array" to return an array of values, which can then be
    examined or processed in an application-dependent manner.

    This having been said, comments and additions (especially if accompanied
    by code!) to Games::Dice are welcome. So, using the above example, if
    anyone wishes to contribute a function along the lines of roll_feng_shui
    to become part of Games::Dice (or to support any other style of die
    rolling), you can contribute it to the author's address, listed below.

PERL VERSION
    This module should work on any version of perl still receiving updates
    from the Perl 5 Porters. This means it should work on any version of
    perl released in the last two to three years. (That is, if the most
    recently released version is v5.40, then this module should work on both
    v5.40 and v5.38.)

    Although it may work on older versions of perl, no guarantee is made
    that the minimum required version will not be increased. The version may
    be increased for any reason, and there is no promise that patches will
    be accepted to lower the minimum required perl.

NAME
AUTHORS
    *   Philip Newton <pne@cpan.org>

    *   Ricardo Signes <cpan@semiotic.systems>

CONTRIBUTORS
    *   Mario Domgoergen <mdom@taz.de>

    *   Mark Allen <mrallen1@yahoo.com>

    *   Ricardo Signes <rjbs@semiotic.systems>

COPYRIGHT AND LICENSE
    This software is Copyright (c) 1999 by Philip Newton.

    This is free software, licensed under:

      The MIT (X11) License

