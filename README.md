# CGI::Untaint::CountyStateProvince

Validate a state, county or province in a
CGI script.

# VERSION

Version 0.05

# SYNOPSIS

CGI::Untaint::CountyStateProvince is a subclass of CGI::Untaint used to
validate if the given user data is a valid county/state/province.

This class is not to be instantiated, instead a subclass must be
instantiated. For example [CGI::Untaint::CountyStateProvince::GB](https://metacpan.org/pod/CGI::Untaint::CountyStateProvince::GB) would
validate against a British county, [CGI::Untaint::CountyStateProvince::US](https://metacpan.org/pod/CGI::Untaint::CountyStateProvince::US)
would validate against a US state, and so on.

    use CGI::Info;
    use CGI::Untaint;
    use CGI::Untaint::CountyStateProvince;
    # ...
    my $info = CGI::Info->new();
    my $params = $info->params();
    # ...
    # Country table(s) must be loaded after CGI::Untaint::CountyStateProvince
    if($params->{'country'} == 44) {
        require CGI::Untaint::CountyStateProvince::GB;

        CGI::Untaint::CountyStateProvince::GB->import();
    } elsif($params->{'country'} == 1) {
        require CGI::Untaint::CountyStateProvince::US;

        CGI::Untaint::CountyStateProvince::US->import();
    } else {
        die 'Unsupported country ' . $params->{'country'};
    }
    my $u = CGI::Untaint->new($params);
    my $csp = $u->extract(-as_CountyStateProvince => 'state');
    # $csp will be lower case

# SUBROUTINES/METHODS

## is\_valid

Validates the data.

# AUTHOR

Nigel Horne, `<njh at bandsman.co.uk>`

# BUGS

Please report any bugs or feature requests to `bug-cgi-untaint-countystateprovince at rt.cpan.org`, or through
the web interface at [http://rt.cpan.org/NoAuth/ReportBug.html?Queue=CGI-Untaint-CountyStateProvince](http://rt.cpan.org/NoAuth/ReportBug.html?Queue=CGI-Untaint-CountyStateProvince).  I will be notified, and then you'll
automatically be notified of progress on your bug as I make changes.

# SEE ALSO

CGI::Untaint

# SUPPORT

You can find documentation for this module with the perldoc command.

    perldoc CGI::Untaint::CountyStateProvince

You can also look for information at:

- RT: CPAN's request tracker

    [http://rt.cpan.org/NoAuth/Bugs.html?Dist=CGI-Untaint-CountyStateProvince](http://rt.cpan.org/NoAuth/Bugs.html?Dist=CGI-Untaint-CountyStateProvince)

- AnnoCPAN: Annotated CPAN documentation

    [http://annocpan.org/dist/CGI-Untaint-CountyStateProvince](http://annocpan.org/dist/CGI-Untaint-CountyStateProvince)

- CPAN Ratings

    [http://cpanratings.perl.org/d/CGI-Untaint-CountyStateProvince](http://cpanratings.perl.org/d/CGI-Untaint-CountyStateProvince)

- Search CPAN

    [http://search.cpan.org/dist/CGI-Untaint-CountyStateProvince](http://search.cpan.org/dist/CGI-Untaint-CountyStateProvince)

# ACKNOWLEDGEMENTS

# LICENSE AND COPYRIGHT

Copyright 2012-2017 Nigel Horne.

This program is released under the following licence: GPL
